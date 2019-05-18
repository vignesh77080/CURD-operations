# CURD-operations-with-tables

<html>
	<head>
		<title>my project</title>
		<script type="text/javascript">
		
		function create_content(){
			var my_form = document.getElementById('myform');
			tab_one = document.getElementById('mytab');
			var tab = document.getElementById('mytab').insertRow(0);
			var att = document.createAttribute('border');
			att.value ='1px';
			tab_one.setAttributeNode(att);
			var len = my_form.length;
			var i ;
			for (i = 0 ;i < len - 1 ; i++ ){
				var val_a = document.querySelectorAll("[type='text']");
				var x = tab.insertCell(i);
				x.innerHTML = val_a[i].value;
		
			}
			var y = tab.insertCell(len-1);
			var edit = document.getElementById('mytab').rows[0].cells[len-1];
			edit.innerHTML = '<a> edit </a>';
			var row = tab_one.getElementsByTagName('tbody')[0].getElementsByTagName('tr');	
			var len_row = row.length;
			for(j=0 ; j < len_row ; j++){
				 row_ind = row[j].rowIndex;
			}
			var chi = edit.firstChild	;
			chi.setAttribute('id','demo'+row_ind);	
			chi.setAttribute('onclick','edit_content(this)')	
		}

		function edit_content(ele){
			var ele = ele = ele.id.toString().slice(-1);
			 row_las = Number(ele);
			console.log(row_las);
			var tab = document.getElementById('mytab');
			var c = tab.rows[row_las].cells.length;
			for( k= 0 ; k < c-1; k++ )
			{
			var my = document.getElementById('myform');
			var val_a = my.querySelectorAll("[type='text']");
			val_a[k].value = tab.rows[row_las].cells[k].innerHTML;
			}
			return row_las;
			
		}

		function upadte_content(){
			var tab = document.getElementById('mytab');		
			var my_form = document.getElementById('myform');
			var cc = row_las;
			var len = tab.rows[cc].cells.length;
			for (z = 0 ;z < len-1 ; z++){
				var val_a = my_form.querySelectorAll("[type='text']");
				tab.rows[cc].cells[z].innerHTML = val_a[z].value;
			}

		}

		function delete_content(){
			var local = row_las;
			var tab = document.getElementById('mytab');	
			tab.deleteRow(local);
		}

		</script>
		<style>
		tr,td {
		width: 260px;
    height: 20px;
    text-align: center;
		}
		tbody {
    width: 75px;
		}
		table#mytab {
    border-collapse: collapse;
		}
		a{
			cursor: pointer;
			text-decoration: underline;
			color: #0000ee;
		}
		</style>
	</head>
	<body>

		<form method='post' action='#' id='myform'>
			<input id='suma0'  type='text' placeholder='name'>
			<input id='suma1'  type='text' placeholder='e-resizename'>
			<input id='suma2'  type='text' placeholder='manifest-name'>
			<input id='suma3'  type='text' placeholder='icon-name'>
			
			<input type='button' id='but_last' value='ok' onclick='create_content()'>
			
			</form>
			<input type='button' id='but_update' value='upate' onclick='upadte_content()'>
			<input type='button' id='but_del' value='delete' onclick='delete_content()'>
			<table id="mytab"></table>
	</body>
</html>


