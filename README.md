# FrontEndRule
根据自身实践所总结出来的前端规范，希望得到评价与补全



##一、基本原则

 1. 统一**两个空格**缩进，不要使用TAB或TAB、空格混搭（大部分编辑器可设置一个tab键代替几个空格）
 2. 省略外链资源（图片及其它媒体资源）URL 中的 http / https 协议，如：
 
    ```
    <!-- Recommended -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
	<!-- Not recommended -->
	<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>
   
   ```

 3. 注释

 	* HTML
 	
 		模块注释：
 		
 		```
 			<!-- 文章列表列表模块 -->
			<div class="article-list">
			...
			</div>
 		```
 		
 		区域注释：
 		
 		```
 		<!--
			@name: Drop Down Menu
			@description: Style of top bar drop down menu.
			@author: whao
		-->
 		```
 		
 	* CSS

 		- 注释统一用'/* */'（scss中也不要用'//'），具体参			照下边的写法；
 		- 缩进与下一行代码保持一致；
 		- 可位于一个代码行的末尾，与代码间隔一个空格。
 		
 		```css
 		/* Modal header */
		.modal-header {
		    ...
		}
		
		/*
		 * Modal header
		 */
		.modal-header {
		    ...
		}
		
		.modal-header {
		    /* 50px */
		    width: 50px;
		
		    color: red; /* color red */
		}
 		```
 	* JS
 		- 单行注释
 			- 双斜线后，必须跟一个空格；
 			- 缩进与下一行代码保持一致；
 			- 可位于一个代码行的末尾，与代码间隔一个空格。
 			
 			```javascript
 			if (condition) {
		    	// if you made it here, then all security checks passed
		    	allowed();
			}
		
			var zhangsan = 'zhangsan'; // one space after code
 			```
 		- 多行注释 
			- 最少三行, '*'后跟一个空格，具体参照下边的写法，建议在以下情况下使用
			- 难于理解的代码段
			- 可能存在错误的代码段
			- 浏览器特殊的HACK代码
			- 业务逻辑强相关的代码
			
			```javascript
			/*
			 * init
			 */
			var x = 1;
			```
		- 文档注释
			各类标签@param, @method等请参考 [JSDoc Guide]
			复杂函数需要注释好函数的作用以及各参数
			
			```
			/**
			 * @func
			 * @param {string} a - 参数a
			 * @param {number} b=1 - 参数b默认值为1
			 * @param {object} c - 参数d为一个对象
			 */
			function foo(a, b, c) {}
			```
 	
 	
 
 
 
 ## 二、HTML
 
 	#### 1. 语法
 		
	 * 缩进使用soft tab（4个空格）
	 * 嵌套的节点应该缩进
	 * 在属性上，使用双引号，不要使用单引号
	 * 属性名全小写，用中划线做分隔符
	 * 文件应以"<!DOCTYPE … …>"首行顶格开始，推荐使用"<!DOCTYPE HTML>"
	 * 必须声明文档的编码charset，且与文件本身编码保持一致，推荐使用UTF-8编码
 		 
 	#### 2. 属性顺序
 	
 	属性应该按照特定的顺序出现以保证易读性：
 	
 	* id
 	* class
 	* name
 	* data-*
 	* src, for, type, href, value , max-length, max, min, pattern
 	* placeholder, title, alt
 	* aria-*, role
 	* required, readonly, disabled 
 
  #### 3. 遵循HTML标准和语义
  在编写HTML代码时，使用语义化标签，避免多余的父节点；
  要用尽量小的复杂度和尽量少的标签来解决问题。
  
  #### 4. 结构、表现、行为三者分离，避免内联
  
  * 使用link将CSS文件引入，并置于head中
  * 使用script将JS文件引入，并置于body底部

  
  ## 三、CSS
  
  #### 1. 书写格式
  
  * 使用4个空格缩进
  * 避免选择器嵌套层级过多，尽量少于3级
  * 以下情况需要换行：

		- ' { '后和' } '前
		- 每个属性独占一行
		- 多个规则的分隔符','后
  * 以下情况需要空行：
		
		- 文件最后保留一个空行
		- '}'后最好跟一个空行，包括scss中嵌套的规则
	* 颜色16进制用小写字母、简写
	* 

  #### 2. 命名规则
  
  * 使用语义化、通用的命名方式
  * 使用连字符 - 作为 ID、Class 名称界定符，不要驼峰命名法和下划线
  * scss中的变量、函数、混合、placeholder采用驼峰式命名
 
 
 #### 3. 缩写属性
 
 CSS提供了各种缩写属性（如 font 字体）应该尽可能使用，即使在只设置一个值的情况下。
 
 ```css
 /* 不推荐 */
 border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;
 ```
 
 ```css
  /* 推荐 */
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
 ```
 
 #### 4. 书写顺序
 为了保证更好的可读性和可扫描重要。作为最佳实践，我们应该遵循以下顺序：
 
 	1）结构性属性：

	* display
	* position, left, top, right etc.
	* overflow, float, clear etc.
	* margin, padding

	2）表现性属性：

	* background, border etc.
	* font, text

#### 5. 结构与样式分离
减少重复的代码精简CSS，提高代码复用性，如

```css
/*not good*/
.btn-primary{
	width: 100px;
	height: 50px;
	padding:5px 3px;
	background: #ccc;
	color: #000;
}

.btn-delete{
	width: 100px;
	height: 50px;
	padding:5px 3px;
	background: #888;
	color: #fff;
}
/*good*/
.btn{
	width: 100px;
	height: 50px;
	padding:5px 3px;
}

.primary{
	background: #ccc;
	color: #000;
}

.delete{
	background: #888;
	color: #fff;
}
```

#### 5. 其他

* 不允许有空的规则
* 元素选择器用小写字母
* 去掉小数点前面的0
* 去掉数字中不必要的小数点和末尾的0
* 属性值'0'后面不要加单位


## 四、JS


#### 1.命名

* **变量、函数、函数的参数、类的方法属性**使用骆驼命名法

	```javascript
	var loadingModules = {};
	```
* **私有属性、变量和方法**以下划线 _ 开头

	```javascript
	var _privateMethod = {};
	```
* **常量**, 使用全部字母大写，单词间下划线分隔的命名方式

	```javascript
	var CLICK_SUM = 100;
	```
* 命名语法
	- **类名**，使用名词。
		```
		function Engine(options) {}
		```
	- **函数名**，使用动宾短语
		```
		function getStyle(element) {}
		```
	- boolean 类型的变量使用 is 或 has 开头。
		
		```javascript
		var isReady = false;
		var hasMoreCommands = false;
		```
	- 构造函数，大写第一个字母

		```javascript
		function Person(name) {
		    this.name = name;
		}
		```
	- jquery对象必须以'$'开头命名
	```
	var $body = $('body');
	```

	

#### 2.声明
一个函数作用域中所有的变量声明提到函数首部，除了for (...)里面使用的一次性变量。var的数量不做限制，但要统一，一行定义一个变量。

#### 3. 数组、对象
* 对象属性名不需要加引号；
* 对象以缩进的形式书写，不要写在一行；
* 数组、对象最后不要有逗号。

```javascript
// not good
var a = {
    'b': 1
};

var a = {b: 1};

var a = {
    b: 1,
    c: 2,
};

// good
var a = {
    b: 1,
    c: 2
};
```

#### 4. 空格
* 数值操作符(如, +/-/*/% 等)、比较符（大于、小于、等于）两边留空格；
* 逗号、冒号、分号后要留一个空格（如果后面还有内容的话）；
* 行尾不要有空格;
* 点号前后不要出现空格；
* 函数名末尾和左括号之间不要出现空格

```javascript

// not good
++ x;
y ++;
z = x?1:2;

// good
++x;
y++;
z = x ? 1 : 2;

// not good
var a = [ 1, 2 ];

// good
var a = [1, 2];

// not good
var a = ( 1+2 )*3;

// good
var a = (1 + 2) * 3;

// not good
for(i=0;i<6;i++){
    x++;
}

// good
for (i = 0; i < 6; i++) {
    x++;
}
```


#### 5. 书写习惯

* 使用两个空格缩进
* 单行过长应在适当位置予以换行,增强可读性，长字符串拼接用加号。
* 句末必须使用分号结束
* if、while、for、do语句的执行体总是用"{"和"}"括起来，即使在其结构体内只有一条语句
* 语法意义相互独立的代码将用空行分隔
* JSON对象的最后一个字段、数组最后一个元素后面都不能加','
* 字符串拼接在少量(次数为个位数)的情况下可以使用'+', 大量的时候使用数组 join(), 或者尽可能采用模板引擎渲染：比如jsRender等
* 不要使用魔法数字，尽量定义一个常量来表示该数字，并加上相应的注释，否则后期可能出现因为数字变化而导致牵一发而动全身，需要到处修改，增加维护成本

	```javascript
	//如汇率换算
	//not god
	dollarPrise = 6.5*price;
	
	//good
	var RATE_USA = 6.5;
	dollarPrise = RATE_USA*price;
		
	```
* 不要直接使用undefined进行变量判断；使用typeof和字符串'undefined'对变量进行判断。
* 用 === ,  !== 代替'==', '!='

#### 6.代码格式化
建议使用jsformat插件使代码格式化，易于阅读


 
 [JSDoc Guide]:[http://yuri4ever.github.io/jsdoc/#@file]

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 