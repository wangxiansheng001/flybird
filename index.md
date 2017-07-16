<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style type="text/css">
		.box{
			position: relative;
			width:200px;
			height:200px;
			border:1px solid #333;
		}
		.box canvas{
			position: absolute;
			top:0;
			left:0;
		}
	</style>
</head>
<body>
	<div class="box">
		<canvas id="canvas" width="200" height="200"></canvas>
		<img id="myimg"/>
	</div>
	
	<script type="text/javascript" src="underscore-min.js"></script>
	<script type="text/javascript">
		var myimg = document.getElementById("myimg");
		myimg.src = "images/" + _.sample(["baby.png" , "liyifeng.png" , "luhan.png","wangjunkai.png","xiaoming.png","yangyang.png"],1)[0];
	</script>

	<script type="text/javascript">
		var canvas = document.getElementById("canvas");
		var ctx = canvas.getContext("2d");

		ctx.fillStyle = "#333";
		ctx.fillRect(0,0,200,200);
		ctx.globalCompositeOperation = "destination-out";

		canvas.onmousedown = function(event){
			this.onmousemove = function(event){
				var x = event.offsetX;
				var y = event.offsetY;

				ctx.beginPath();
				ctx.arc(x,y,30,0,7,false);
				ctx.closePath();
				ctx.fill();
			}
		}

		canvas.onmouseup = function(){
			this.onmousemove = null;
		}
	</script>
</body>
</html>
