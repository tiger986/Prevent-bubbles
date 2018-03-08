## Compatible writing to prevent bubbles
#### HTML code
```html
<div class="d1">
		d1
    <div class="d2">
        d2
       <div class="d3">
           d3
       </div>
	  </div>
</div>
```
#### JS code
```javascript
$(".d1").click(function () {
			alert("d1");
		});
		
		$(".d2").click(function () {
			preventBubble(); //Prevent bubble event call (written in an event)
			alert("d2");
		});
		
		$(".d3").click(function () {
			preventBubble(); //Prevent bubble event call (written in an event)
			alert("d3");
		});
		
		//Prevent bubble events (written in JS) (compatible with IE, Firefox, and Google)
		function preventBubble (event) {  
			var e=arguments.callee.caller.arguments[0]||event; 
			if (e && e.stopPropagation) {  
				e.stopPropagation();  
			} else if (window.event) {  
				window.event.cancelBubble = true;  
			}  
		}
