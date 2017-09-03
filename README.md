记录web前端学习的收获

####### 2017.06.23 ##########  
1. 获取标签宽度  
   HTMLElement.offsetWidth  
   [参考链接](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/offsetWidth "获取标签宽度")  

2. jQuery点击事件失效  
   + 使用 $("#id").click(function(){ }); 有时会失效  
     原因：  
     直接将事件绑定在#id元素上，如果#id元素在绑定后生成，则不会触发改事件  
   + 推荐使用以下形式    

   	```javascript
     $(document).on('click','#id',function(){  
        console.log('document');  
     });  
	```

     原因：  
     将事件绑定在document DOM树下，当事件到达#id元素时，事件程序被执行，由于是从整个document下寻找的，可以保证事件被触发  
     [参考链接](https://stackoverflow.com/questions/14879168/document-onclick-id-function-vs-id-onclick-function "jQuery $(#id).click 和 $(document).on(click,#id,function(){ })区别")  
3. 去除所有情况下a标签的下划线  

	```css
   	a {   text-decoration: none;  }  
   	a:hover, a:visited, a:link {  text-decoration: none; }  
   ```

4. position：static/absolute/relative  
   + static: 默认值，无特殊定位，对象遵循HTML原则;  
   + absolute:   
	 绝对定位，将对象从文档流中拖离出来，使用left/right/top/bottom等属性相对其最接近的一个并有定位设置的父元素进行绝对定位;若没有父元素，则以html、body，浏览器的位置为相对位置，而其层叠通过z-index属性定义;  
   + relative:  
	 相对定位，对象不可层叠，将依据right，top，left，bottom（相对定位）等属性在正常文档流中偏移位置(相对于谁呢？相对于它自己本身，即是在原来位置上偏移，而且注意原有位置就是在保留的);	  
5. 隐藏多余溢出文字并显示省略号的样式  
	```css
    overflow: hidden;  
    white-space: nowrap;  
    text-overflow: ellipsis;   
    ```
6. a标签点击失效，可能的原因是层级问题，被覆盖，解决办法设置定位position:relative和z-index  
7. :hover 改变其他元素样式时，只对子元素和相邻的兄弟元素有作用   
8. if语句为false的几种情况：  
  数字 0   
  非数字 NaN   
  空字符串 ''   
  空指针 null  
  没有定义 undefined  
  false本身   
9. js发生异步的情况：需要等待  [博客整理](http://blog.csdn.net/lizhenqii/article/details/77806681 "博客整理")
	等待的场景有：

		- 定时任务：setTimeout, setInterval  
		- 网络请求：ajax请求，图片img加载等  
		- 事件绑定  

10. 防止浏览器缓存  
	链接加上一个随机数，比如js中用Math.random()  
11. DOM的property和Attribute区别  
	- property是js中对象中的标准属性,DOM.className  
	- Attribute是标签文档中的属性,比如DOM.getAttribute('href')  
12. 给标签添加自定义属性，需要在前面加上'data-'，比如：

	```html
	<a data-mid='2'>加上一个mid自定义属性</a>
	```
13. BOM常见操作  
	1. 判断浏览器类型navigator  

	```javascript
	var ua = navigator.userAgent
	var isChrome = ua.indexOf('Chrome')
	console.log(isChrome)
	```
	2. 获取屏幕宽高screen  

	```javascript
	screen.width
	screen.height
	```
	3. 拆解url各个部分location  
	http://coding.xuan.com/lesson/115.html?id=1#mid=5390  

	```javascript
	location.href //获取整一个连接
	location.protocol //协议类型 http
	location.hash //如 #mid=5390 
	location.search // 获取查询部分，如 ?id=1
	location.pathname // 'lesson/115.html'
	```
	4. 页面回退与前进 history  
	
	```javascript
	history.back()
	history.forward()
	```









    



