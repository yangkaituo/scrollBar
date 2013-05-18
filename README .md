ScrollBar
=========
如何自定义一个滚动条？

scroll.1.html 把滚动条隐藏掉，也就是说scrollbar还在只不过被遮住了，依旧可以拿到scroll事件。

scroll.2.html 如果把可视区域视做一个舞台的话，那么待显示的内容就是一篇幕布，通过控制内容的Top值来实现滚动的效果。

scroll.3.html 通过控制内容的scrollTop值来连动设置滚动条的top值来实现滚动效果。

代码思路
-------

````html
(function($) {
	// 环境函数 检测浏览器以及版本
	function ENV() {
		
	}	
	
	function ScrollBar(content, track, This) {

		// 初始化计算容器的高度、内容的高度、滚动条的高度 
		var init = (function() {
			
		})(); 
		
		//speedToAxis方法是将wheelDelta转换为适当的值
		this.speedToAxis = function(wheelDelta, o) {			
			//设定一个最大值和最小值，让鼠标滚轮最快也不超过这个速度，最慢时也不小于最小值							
			//缓存当鼠标滚动时的最大加速度
			//计算wheelDelta值的偏移量
		}	
		
		//用来控制内容和scrollbar的高度
		this.move = function(i) {			
			//计算content的scrollTop值
			//计算滚动条的top值
			//计算滚动条的上下边界						
		}		
	}
	
	// 为jquery的$扩展一个scrollbar方法
	$.fn.scrollBar = function(content, track) {
		// 例行的参数检查
		// 实例化构造函数 
		// 对浏览器判断 
		
		// 对容器绑定事件
		this.bind(mousewheel, function(e){
			//自定义一个鼠标滚轮加速度的最大值和最小值
	    	//调用speedToAxis方法 加工delta值
			//把计算好后的值传递给move方法 用来设置 content的值和scrollbar的值
		});
	}

})(jQuery);

//为实现滚动条的容器绑定scrollBar方法()
//传递连个参数 第一个为内容的id  第二个为滚动条id
$(document).ready(function() {
	$('#scrollbar_content').scrollBar('scrollbar_content', 'scrollbar_track');
});
````

重点提示
--------
MouseWheel 事件在FF下是DOMMouseScroll事件，而event.wheelDelta的属性在FF也变成了detail. 值得一提的是MouseWheel事件是鼠标滚轮在每转一格的距离，所以它就有一个加速度问题，也就是当鼠标滚轮转动速度越快它每走一格的距离就会变的更大，相反当它速度转的慢时它每走一格的距离就会接近或者等于默认值。鼠标轮转动的时候，我们总能拿到一格最大的值，然后你把当次的值和最大值比较，就能算出一个比例。
首先需要一方法把连续的滚动转换为适当的值，这个值要能直接用于scrollbar的top属性，在speedToAxis方法中设定一个最大值和最小值，让鼠标滚轮最快也不超过这个速度，反之亦然。其次，有一个变量缓存最大加速度。最后，把鼠标轮的值转换为一个标量并且返回。

有任何问题请与我联系：yangkaituo AT gmail.com

或访问我的: http://eclipseongoing.diandian.com/