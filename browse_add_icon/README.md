## Browse Screen: Add Icons in front of text

This will add an icon in front of a text in a browse column using font awesome icons ( https://fontawesome.com/v4.7.0/icons/ )


<p align="left">
  <img src="screenshots/browse_icons.png">
</p>


☛ Add this JavaScript code to your form's Custom Code field

☛ Change the status descriptions, icons, colors in statusArr if necessary.

```
var statusArr = [
	{status:"Pending",class:"fa fa-clock-o",color:"#f1c40f"},             // orange
	{status:"Completed",class:"fa fa-check-circle",color:"#2ecc71"},      // green
	{status:"Cancelled",class:"fa fa-ban",color:"#e74c3c"},               // red	
	{status:"New",class:"fa fa-circle-o",color:"#707070"},                // grey
	{status:"In progress",class:"fa fa-spinner",color:"#3498db"}          // blue
]

function addStatusIconFA(col) {
	
	$("[data-nu-column='"+col+"']").each(function(index) {  
			
		var status  = $(this).html();			

		var index = statusArr.findIndex(x => x.status === status);
		var _class = statusArr[index].class;
		var color = statusArr[index].color;
		
	    $(this).prepend('<i class="'+ _class +'" aria-hidden="true" style="font-size:medium;color:'+color+';"></i>&nbsp;');

	})
}
```

Example: Add a status icon in the first column when the Browse Screen is loaded


```
if (nuFormType() == 'browse') {
   addStatusIconFA(0);
}
```