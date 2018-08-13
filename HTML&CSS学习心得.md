[TOC]

# HTML入门

## 认识HTML
* HTML是一门**标记语言**
* 在HTML编辑器里的缩进和空格并不会在浏览器中显示，浏览器会**忽视制表符、回车和大部分空格**
* HTML注释以\<!--开头，以--\>结尾
* 浏览器元素=开始标记+内容+结束标记 (有些元素相对例外，比如\<img\>)
* 在HTML的头文件里有一个Style标记，可以在其中写CSS

## 深入了解超文本
* 用\<a\>标记来创建超链接， 开始标记内，使用href属性链接到相应的URL或者HTML，内容为可单击文本,在这个元素内你也可以选择重新定义打开页面的标题，通过title属性控制
* 路径可以直接使用URL也可以使用相对路径
* 对于相对路径，'..'表示上一级菜单，'/'分割路径的各个部分
* 对于相对路径，比如`../../fruit.jpg`，就是回到上两级文件夹里寻找fruit.jpg的文件
* \<img\>元素里面的的路径使用src属性控制

## 构建模块
* \<q\>表示短引用，作为现有段落的一部分，然而\<blockquote\>则表示一大段的引用并且**附带缩进**
* 在希望换行的地方插入一个\<br\>（这是一个void元素，它**没有内容，只有一个标记**，当然了\<img\>也是一个void元素）
* 创建列表时，需要把项放在\<li\>元素中，然而我们还需要把列表包裹在\<ol\>（有序列表）\<ul>（无序列表） 中
* \<ol>\<ul>中只包含\<li>元素

## 连接起来
* 域名指的是类似于'google.com'这样的，而网站名则要在域名前加上‘www.’这样的服务器名
* URL的第一部分是互联网协议，第二部分是网站名，第三部分是绝对路径
* 输入域名后，服务器会尝试查找这个目录里的一个默认文件，通常是'index.html'或'default.htm'，并返回给浏览器显示
* 通过id属性，可以设置一个锚点，在使用\<a>元素时，可以直接连接到这个锚点，例如：
`\<a href="index.html#start">start\</a>`或`\<a href="http://www.starbuzz.com/buzz/index.html#coffee">Coffee\</a>`
* 用\<a>元素中的target属性来把链接打开到一个新窗口，你需要把target属性设置为 **_blank**

## 为页面增加图像
* \<img元素中的src元素不仅可以使用相对链接也可以使用URL
* \<img>元素中的alt属性的重要性在于，在图像未正确显示时，可以显示出alt属性里的内容
* \<img>元素中可以通过width和height属性控制大小，但是缺点在于浏览器需要下载全尺寸的图像，然后再缩放。这对于用户来说体验相对较差（因为很慢），所以推荐先使用PS等软件调整好大小后再使用
* 对于点击图像缩略图打开原图的操作，我们可以使用 **\<a>嵌套\<img>元素**，先用\<a>的href链接到原图（可以直接是一个JPG图像也可以是一个创建好的HTML页面），然后再使用\<img>显示缩略图，并且定义好alt属性，然后结束\<a>元素。

# CSS入门

## 认识CSS
* CSS元素的两边**不需要**\<和\>
* CSS规则需要放在\<head>元素的\<style>元素里
* 链接到外部样式表时不需要\<style>元素，但是需要\<link>元素，例如`\<link type="text/css" rel="stylesheet" href="lounge.css">`。type指定了这是一个CSS样式表，rel指定了HTML文件和所链接的文件之间的关系：链接到一个样式表，href则标明了样式表的位置
* 子元素会继承父元素的属性，这一点和各种其他语言类似
* CSS里面的规则与HTML里面的不相同，它以\/\*开头，以\*\/结尾
* 要将HTML里面的元素加入一个类，只需要在元素后加上类属性和类名即可，例如`\<p class="greentea"\>`
* CSS中类选择器的书写方法如下：先选择类中的元素，比如上面的p，然后再用一个.指定一个类，最后是类名，书写出来就是**p.greentea{规则}**，选择一个类中的全部内容可以使用如下写法：**.greentea**
* 元素也可以加入多个类。举个例子，我可以把一个\<h1>放在products类中，在这个类中定义了字体大小和粗细，另外还可以把它放在special类中，在这个类中定义字体颜色。在CSS样式表中，**多个类名写在一个双引号下，用空格分隔开**。

## 增加字体和改变样式

### 增加字体
* 使用font-family属性可以指定字体系列，通常你指定的font-family，包含**一个首选字体，多个候选字体，最后一个通常为一个通用的字体系列名**
* 如果一个字体名包含多个单词，那么你需要在字体名两边加上双引号，例如"Courier New"
* 如果要使用一个Web字体，那么你需要在服务器上托管字体，或者使用一个字体托管服务
* **如何为页面增加一个Web字体？**
    >1. 找到一个Web字体
    >2. 把字体放到服务器上或者使用托管服务
    >3. 在CSS中增加@font-face规则。把这个规则增加到CSS样式表的最上面。格式如下
    >    ```CSS
    >    @font-face{
    >        font-family："Personal One";
    >        src:url("http://......"),
    >            url("http://......");
    >        }
    >    ```
     >4. @font-face告诉浏览器，将要加载src URL下指定的字体文件。浏览器就会尝试加载，知道它找到一个支持的字体文件。一旦加载，会为这个字体分配font-family属性中的名称，在这里就是"Personal One"，然后你就可以在font-family属性中使用你指定的字体名称
     >5. 注意：移动设备和小型设备并不支持Web字体。如果定制多个Web字体的话，需要使用多个@font-face规则，然而每多一个额外的字体，页面加载的时间就会更长一些，我相信你可以明白其中的道理

### 改变样式
* 调整字体大小有四种方式
    * 用像素：14px
    * 用百分比：140%
    * 用比例：1.4em
    * 用关键字：xx-small；x-small；small；medium；large；x-large；xx-large
* **如何方便的指定字体大小？**
    >1. 选择一个关键字，将它设置为body规则中的字体大小。这相当于页面的默认大小
    >2. 使用em或者百分数，相对于body字体的大小指定其他元素的字体大小
    >3. 每个元素都会按比例增大，因为元素的字体大小是相对于body字体大小指定的。实际上这种方法，就是为一个页面定义一个默认的字体大小
* Web颜色的指定有三种方式
    * 按名称指定
    * 按rgb值指定：rgb(80%,40%,0%)
    * 按十六进制码指定：#cc6600
* 在内容下加下划线有两种方式，一种是真的老老实实加underline，另一种使用下边框线
* 如果一个\<em>有两种不同的规则，一个是上划线一个是下划线，他们不会累加，你需要把两个值合并到一个规则中
* 有下划线的文本常常会被误认为是可以点击的链接，所以慎用下划线

## 盒模型
* 从CSS的角度来看，每个元素都是一个盒子，而每个盒子则包含**内容区、内边距、边框、外边距**
* 背景图像可以不重复，只要你把它的background-repeat属性设为no-repeat即可，当然了这个属性有四个可选的值：**no-repeat;repeat-x;repeat-y;inherit**
* 如何只在左边增加内边距？
    >1. 先用四周的内边距设定好（如果有内边距的要求）
    >2. 然后再为左边设置一个padding-left的属性
    >3. **这里的顺序非常重要，如果交换了顺序，就会先设置左边距，然后才将四周的内边距设定出来，这也包括左边（这样一来左边的内边距就被覆盖了）**
* 不同浏览器对边框的关键字thin.medium.thick可能有不同的默认大小
* 在CSS中使用id和使用类基本相似，只是把点号（.）换成了井号（#）
* **类名要以一个字母开头，但是id则以数字或者字母开头，相同之处在于二者都不能包含空格**
* 对于混合样式表，他们的顺序非常重要，这些样式表从上往下排列，但是**最下面的样式表最优先**。

## 媒体查询
* 在HTML中使用媒体查询很简单，只需要在link元素中增加一个media属性即可，例如`media="screen and (max-device-width: 480px)"`,这一行代码意味着，只在有屏幕而却屏幕宽度不超过480px的设备上显示
* 在CSS中使用媒体查询也很简单，我们需要在CSS中新建一条规则，下面给出一条例子
    ```CSS
    @media screen amd (min-device-width: 481px) {
        #paragarph {margin-right: 250px;}
    }/*这里首先使用@media规则，在规则后面接上媒体查询条件，首先是带有屏幕其次是最小宽度是481px，对于与前面设备条件screen匹配的设备，将所有条件写在后面的大括号内。*/
    @media screen and (max-device-width: 480px) {
        #paragraph {margin-right: 30px;}
    }
    @media print {
        body{
            font-family:Times,"Times New Roman",serif;
        }
    }/*如果要打印这个页面，则会使用这些规则*/
    p.specials{
        color: red;
    }/*其他所有规则会应用于所有界面，因为他们未被包含在@media规则中*/
    ```

# 高级Web建设

## Web与Span
* \<div>元素允许将页面划分为几个逻辑区
* 可以给div指定id从而在CSS选择器中选中
* width属性只指定内容区的宽度
* text-align会对块元素中的所有内联内容都居中处理。尽管这个属性的名字叫text-align但是实际上它作用于所有的内联内容，**包括图像**
* 对于CSS的子孙选择器，从左到右依次为父+空格+子……以此类推
* 对于行高的设定，如果对一个包含标题的类直接使用比例设定的话，标题也会继承原本设定给正文的行高，所以如何修复标题的行高就成了一个问题。**然而line-height这个属性有点特殊，它除了可以使用百分比、关键字、比例这三种值之外，还可以直接接受一个数。如果接受了一个数比如1，就表示行高是其自身字体大小的一倍**
* 简写内外边距的两种方式以及边框属性和背景的简写
    ```CSS
    padding: 0px 20px 30px 10px;/*从左到右依次是：上右下左*/
    margin: 0px 20px;/*从左到右依次是：上和下，左和右*/
    border: thin solid #007e7e;/*这个属性接受的值无所谓顺序*/
    background: white url(images/cocktail.gif) repeat-x;/*同样无所谓顺序*/
    ```
* \<div>允许用户对块级内容进行逻辑划分，但是\<span>则允许用户对内联内容进行逻辑划分
    ```HTML
    <span class="cd">Buddha Bar</span>,<span class="artist">Claude Challe</span>
    <span class="cd">When It Falls</span>,<span class="artist">Zero 7</span>
    ```
    只要你设定好span的id，就可以通过CSS统一的指定一个id下的样式,这样也就变相的达到了**给内联元素分组**的目的
* \<a>元素是创建超链接的一个元素。对于链接，我们知道它有三个状态**未访问、已访问、悬停**，对于每种状态我们都可以通过CSS控制样式。切记：注意用户友好
    ```CSS
    a:link{
        color: green;
    }/*未访问*/
    a:visited{
        color: red;
    }/*已访问*/
    a:hover{
        color: yellow;
    }/*光标悬停在上面，显示HTML的title信息*/
    ```
* 浏览器确定一个元素使用哪个样式时，
    1. 它会先收集所有的样式表，然后按**作者的样式->读者的样式->浏览器的默认样式**进行排列
    2. 找出所有与这个元素匹配的样式
    3. 对所有匹配的规则按1的顺序排列
    4. 然后按特定性对3种排列好的规则排序
    5. 对于冲突的规则，按照它们在各自样式表种出现的顺序进行排序并且选取第一个规则

## 布局与定位

### 浮动布局
* 各个块元素都是从页面的上方流向下方，元素之间都会有一个换行。内联元素从元素的内容区的左上方流向右下方
* 浏览器并排放置两个块元素时，外边距会相加。而当浏览器上下放置两个块元素时，他们共同的外边距为两个外边距较大者
* **如何浮动一个元素？**
    >1. 指定标识，因为我们只想让某一个块元素浮动，并不是某一类块元素
    >2. 指定一个宽度。对于每个浮动元素都会有一个要求：它必须有个宽度，通过width来设置
    >```CSS
    >#fudong{
    >    width: 200px;
    >}
    >```
    >3. 通过float属性让他浮动
    >```CSS
    >#fugong{
    >    width: 200px;
    >    float: right;
    >}
    >```
    >4. 由于这个浮动段落已经从正常的流中删除，所以其他元素就流上来了。不过，**对浮动的这个段落定位时，他们会围绕这个浮动段落的边界，因此会围绕着浮动元素**，可以想象为浮动元素是被块元素忽略的元素，但是内联元素缺知道它在哪（内联元素会留意浮动元素的边界，但是块元素会正常的流向页面）
* 对于浮动元素，如果它在未浮动时位置靠后，那么在页面大部分元素排列完后才会浮动这个元素，反之就时先浮动元素再排列其他剩下的
* 注意，浮动元素的宽度是固定的，因为在浮动之前，我们已经通过CSS对它的宽度进行了定义。所以对于某些试图通过浮动主内容而不是侧边栏的想法，有时是不可取的。因为当我们在改变浏览器宽度时，主内容的宽度是不变的，在某些情况下，这并不美观
* 遇到浮动元素遮挡了某些某些流中的元素时（主要是因为浮动元素太长而流中的元素又太短，所以遮挡到下一个流中的元素），我们可以使用CSS中的clear属性。它有4个可选的值：none|left|right|both。none:默认值；left:左侧抗浮动；right:右侧抗浮动；both:两侧都抗浮动。**具体的实例参考[准确理解CSS clear:left/right的含义及实际用途](https://app.yinxiang.com/shard/s46/nl/21149758/98442513-9d75-4c8c-9e19-2724cdac3513)**
* 内联元素也可以浮动。最好的例子就是浮动图像。可以尝试一下，将图像在段落中向左或者向右浮动，你会看到文本都会围绕在它周围。

### 冻结布局和凝胶布局
* 对于冻结布局，只需要创建一个新的\<div>就可以了，示例代码如下所示：
    ```HTML
    <body>
        <div id="allcontent"> <!--───────────────┐这个div将包含<body>中所有其他元素-->
            <div id="header">                <!--|-->
            ...the rest of HTML goes here    <!--|-->
            </div>                           <!--|-->
        </div> <!--<─────────────────────────────┘-->
    </body>
    ```
    这样设置完成之后，**无论浏览器怎么调整大小，整个布局都不会移动**
* 另外我们还有一种布局叫凝胶布局，这种布局介于冻结和流动之间，具体代码如下所示（基于上一条冻结布局的代码修改而来）：
    ```CSS{.line-numbers}
    #allcontent{
        width: 800px;
        padding-top: 5px;
        padding-bottom: 5px;
        background-color: #675c47;
        margin-left: auto;
        margin-right: auto;
    }
    ```
    **当L6和L7两个属性的值设置为auto时，浏览器会确定正确的外边距是多少，另外还会确保左和右外边距相同，并且将所有内容居中**

### 绝对布局（绝对定位）
这里介绍一种形式和浮动元素相仿的手法：绝对定位，这个手法可以在页面上精确的定位元素，先给出示例代码：
```CSS
#sidebar{
    position: absolute;/*用这个属性指定这个元素将要被绝对定位*/
    top: 100px;
    right: 200px;/*边栏定位在距离页面右边200px，距离页面顶部100px的位置上*/
    width: 200px;/*指定宽度200px*/
    }
```
* 由于边栏这个元素时绝对定位的，所以它会从流中删除，并根据top、right、left或者bottom属性来定位。**而且流中的元素不会将其内联内容围绕在一个绝对定位的元素周围，你可以认为他们完全不知道页面上还有一个绝对定位的元素，也就是说我们不能再使用clear属性了**
* 同时每个定位元素都会有一个z-index属性，元素越“靠近”你，z-index的值会越大
* position的默认值是static（静态）。如果是静态的话，元素会放在正常的流中，而不是由你来指定位置，要由浏览器来决定这些静态定位元素放在哪里。**你大可以使用float属性将一个元素从流中取出，但是最终让然由浏览器来决定这个元素放在哪里。然而使用“absolute”值时，将由你来告诉浏览器这个元素放在哪里**
* 对于position属性，它还有fixed和relative两个值。[fixed](#fixed)（固定）定位时将元素放在 **相对于浏览器窗口的一个位置上（而不是相对于页面）**，所以固定元素永远也不会移动，你将会在后面的内容里看到相关的例子。而对于relative（相对）定位，它则会让元素正常地流入页面，不过**在显示在页面上之前，会进行偏移**，这相当于更高级的定位和特殊效果
* **可以对任何元素都可以使用绝对定位，包括块元素和内联元素。但是切记：一个元素绝对定位时，会把他从正常的流中删除**

### 表格显示
* 对于CSS表格，每个单元格会包含一个HTML块元素，表格会自动扩展来适应单元格宽度和高度
* 创建一个表格的步骤如下
    1. 创建一个\<div>表示整个表格，行和列都会嵌套在这个\<div>中
    2. 对于表格中的**每**一行，创建一个\<div>
    3. 对于每一列，只需要一个块元素作为该列内容即可
    4. 示例代码如下
        ```HTML
        <div id="tableContainer"><!--这是一整个表格的div-->
            <div id="tableRow"><!--这是一行-->
            <div id="main"><!--这是第一列-->
                <!--code gose here-->
            </div>
            <div id="sidebar"><!--这是第二列-->
                <!--code gose here-->
            </div>
            </div>
            </div><!--注意嵌套-->
        ```
* 用CSS样式表控制样式（以上示例代码为例）
    1. 首先，为表格增加一个\<div>，id为tableContainer，这个\<div>包含行和列
        ```CSS
        div#tableContainer{
            display: table;
        }
        ```
    2. 接下来，为行增加一个\<div>，id为tableRow。从前面的示例代码可知，我们只有一行，所以只需要一个行\<div>。**如果有多个行，就需要多个行\<div>了**
        ```CSS
        div#tableRow{
            display: table-row;
        }
        ```
        我们的表格中只有一行，所以我们使用了id，如果你有很多行，建议你使用一个类（例如div.tableRow），而不是id，这样就可以用一个规则指定所有行的样式

    3. 最后，使用现有的"main"和"sidebar" \<div>作为单元格，对应行中的第一列和第二列
        ```CSS
        #main{
            display: table-cell;
            background: #efe5d0 url(images/background.gif) top left;
            font-size: 105%;
            padding: 15px;
            margin: 0px 10px 10px 10px;
        }
        #sidebar{
            display: table-cell;
            background: #efe5d0 url(images/sidebar.gif) bottom right;
            font-size: 105%;
            padding: 15px;
            margin: 0px 10px 10px 10px;
        }
        ```
    4. 对代码做出进一步修改:
        ```CSS
        div#tableContainer{
            display: table;
            border-spacing: 10px;
        }
        div#tableRow{
            display: table-row;
        }
        #main{
            display: table-cell;
            background: #efe5d0 url(images/background.gif) top left;
            font-size: 105%;
            padding: 15px;
            vertical-align: top;
        }
        #sidebar{
            display: table-cell;
            background: #efe5d0 url(images/sidebar.gif) bottom right;
            font-size: 105%;
            padding: 15px;
            vertical-align: top;
        }
        ```
        通过对比上面第三点的代码，我们会发现，在tableContainer规则下增加了一条border-spacing属性，这个属性为表格中的单元格增加10px的边框间距，所以我们不再需要\<div>上的外边距（见#main和#sidebar），注意：**其他块元素的边距不会和表格的边框间距叠加**，所以调整完表格的边框间距之后，我们需要适当的调整其他块元素的边距。另外我们需要确保两个单元格中的**所有内容都是相对于单元格上边对齐**，所以增加了vertical-align属性和相关的值

### <div id=fixed>固定定位</div>
* 注意，固定定位是**距离浏览器窗口**来进行的偏移
* 示例代码如下：
    ```CSS
    #coupon{
        position: fixed;
        top:300px;
        left: 100px;
    }
    ```
    此处top/left的值都可以是负数，当你设定为负数时，元素会**向浏览器边界外偏移**

## HTML5标记
* 新的HTML5标记明确了人们利用\<div>创建页面的方式，并且提供了更特定、更适合某些结构的标记
    * \<section>用于对相关内容进行分组
    * \<article>用于类似博客帖子、论坛帖子和新闻报道等独立的内容
    * \<aside>用于表示不作为页面主内容的次要内容，如插图和边栏
    * \<nav>用于组织网站导航链接
    * \<header>将标题、logo、署名等通常放在页面或区块最上方的内容组织在一起
    * \<footer>将诸如文档信息、法律措辞和版权说明等通常放在页面或者区块下方的内容组织在一起
    * \<time>用来标记时间和日期
    * \<div>仍然用来建立结构。
    * \<video>用于为页面增加视频
* 把相应的\<div>替换成上面的关键字即可，但是要记住，因为你修改了新的标记，CSS样式表也要做出相应的更改。

### \<section>和\<article>
* 区块（section）和文章（article）有什么区别？
    > 区块可以把相关的内容分组在一起，但是文章包含独立的内容，如一个新闻报道、一个博客帖子或者一个简短的报告。我的意思是说可以像下面这样：
    > ```HTML
    > <section id="blog">
    >   <article>
    >       <h1>title1</h1>
    >       <p>content1</p>
    >   </article>
    >   <article>
    >       <h1>title2</h1>
    >       <p>content2</p>
    >   </article>
    > </section>
    > ```
    > **区块可以包含很多文章，但是文章真的只是一篇文章**。要组织独立的内容，就要使用区块，而对于独立的内容就要使用文章。如果你需要**把感觉不相关的内容组织在一起，往往可以使用\<div>作为后备**

### \<time>
\<time>中有一个十分重要的属性：datetime，正是因为它重要，我觉得有必要了解一些具体的事项
1. 先给出示例代码：`<time datetime="2018-08-11">08/11/2012</time>`
2. datetime后面跟的是指定日期的官方Internet日期格式，当然了这个格式还有很多，见图![official Internet formats for dates](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/official%20internet%20formats%20for%20dates.png)
3. 如果元素内容没有采用官方格式进行书写，就必须使用datetime属性来自定义格式了。这样我们就可以指定一个日期或者时间，来写我们希望的任何元素内容，通常是某个和时间有关的信息，例如"yesterday"\\"now"\\"Aug 11,2018"

### \<header>
* \<header>元素并不仅仅用于主页眉，如果你希望把一些元素组合起来放在首部，你也可以使用\<header>。例如，可以为\<article>,\<section>,甚至\<aside>增加\<header> 元素。最常见的例子就是在一篇博文里，通过\<header>把\<h1>和\<time>组合为一个首部。例如：
    ```HTML
    <article>
        <header>
            <h1>title</h1>
            <time datetime="2018-08-11">08/11/2018</time>
        </header>
        <p>content</p>
    </article>
    ```
* 对于多个\<header>，**要注意使用id或类来区分**，我相信页面的主页眉和文章的页眉样式是不同的。通过id或类来区分，会使你的CSS样式表写起来更加方便，用起来也更加美观

### \<nav>
**导航栏的本质是一个无序列表**，通过CSS更改样式，让它长得比较像一个导航，下面我们来看两段示例代码，一段是HTML，一段则是CSS
```HTML
<nav>
    <ul>
        <li><a href="index.html">HOME</a></li>
        <li class="selected"><a href="blog.html">BLOG</a></li>
        <li><a href="">INVENTIONS</a></li>
        <li><a href="">RECIPES</a></li>
        <li><a href="">LOCATIONS</a></li>
    </ul>
</nav>
```
```CSS
nav {
    background-color: #efe5d0;
    margin: 10px 10px 0px 10px;
}/*增加了一个新规则，将设置背景颜色和外边距的属性移到这个规则中，这样<nav>中所有的元素都会继承这个样式*/
nav ul {
    margin: 0px;/*这里设置了一个属性，将<ul>的外边距设置为0，使得它能紧贴着放在<nav>元素中（否则默认情况下，如果没有明确设置为0px，<ul>会有一个外边距，这会让<ul>稍稍偏移）*/
    background-color: #efe5d0;
    margin: 10px 10px 0px 10px;
    list-style-type: none;/*删除了列表项的项目符号*/
    padding: 5px 0px 5px 0px;
}
nav ul li {
    display: inline;/*block改为inline，是为了让列表项前后都不再有回车，这意味着他们会流入一行*/
    padding: 5px 10px 5px 10px;
}
nav ul li a:link, nav ul li a:visited {
    color: #954b4b;
    border-bottom: none;
    font-weight: bold;
}/*我们希望导航列表中的链接看起来和页面内的其他链接有所不同，所以这里覆盖了<a>的其他规则，这个规则会为link和visited状态的链接设置属性，让他们看起来相同*/
nav ul li.selected {
    background-color: #c8b99c;
}/*最后，为"selected"类的<li>元素设置背景，这样一来，如果某个导航正在对应我们所在的页面，他看起来会和其他导航项目有所不同*/
```

### \<video>
* \<video>元素确实很像\<img>元素，我们先来看一段代码：
    ```HTML{.line-numbers}
    <video controls
        autoplay
        width="512"
        height="288"
        src="video/video1.mp4"
        poster="images/poster.png"
        id="video">
        </video>
    ```
    上面这段代码里，包含了很多细节，我们一一来看：
    1. 如果存在controls属性，播放器会提供一些控件，可以控制视频和音频的播放
    2. 如果存在autoplay属性，一旦页面加载，视频就开始播放
    3. 注意：上面两个属性都是我们在这里新接触的**布尔属性**，没有值，但是如果存在便是真，不存在便是假
    4. 在L3和L4,分别定义了页面中视频的宽度和高度
    5. L6是一个可选属性，如果视频未播放，就会显示这个封面
    6. 另外，还有一些这里没有提到的属性：
        * loop：这也是一个布尔属性。如果存在，视频结束播放之后会自动重新开始播放
        * preload：这个属性通常用于控制视频如何加载来实现优化。大多数情况下，浏览器会根据是否设置autoplay以及用户的带宽来选择加载多少视频，然而这个属性可以覆盖上面的设置，将preload设置为“none”（在用户真正“播放”视频之前不下载视频），也可以设置为“metadata”（下载视频元数据，但是不下载视频内容），或者设置为“auto”，交给浏览器来做决定
* HTML5规范允许采用任何视频格式，具体支持哪些格式由浏览器决定：
    * 对于Safari，应该使用.mp4（含H.264格式的视频）
    * 对于Chrome，应该使用.webm
    * 对于Firefox或者Opera，应该使用.ogv
* 对于上面这种情况，我们可以在\<video>元素中对应每种格式提供多个\<source>元素，可以让浏览器选择支持的格式，示例代码如下：
    ```HTML
    <video controls
        autoplay
        width="512"
        height="288" >
        <source src="video/video.mp4">
        <source src="video/video.webm">
        <source src="video/video.ogv">
        <object data="video/video.swf"></object>
        <p>sorry,your browser doesn't support the video element</p>
    </video>
    ```
    在这里，注意到我们**从\<video>中删除了src属性，然而换成了多个\<source>标记**，每个标记有各自的src属性，分别包含不同格式的视频。如果浏览器不支持所有提供的格式，会先使用\<object>，用户会看到播放flash视频，如果也无法使用，就会显示\<p>元素中的文本

## 建立表格
在这一节开始前，我们需要明白，这一节的表格是使用HTML表示它的表格数据，而不是通过CSS建立布局（那属于表现范畴）

### 创建一个表格
1. 使用HTML创建一个表格，在这里先给出示例代码，然后我们再来一一解释
    ```HTML{.line-numbers}
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <style type-"text/css">
            td, th {border:1px solid blank;}
        </style>
    </head>
    <body>
        <table>
            <tr>
                <th>City</th>
                <th>Date</th>
                <th>Temperature</th>
                <th>Altitude</th>
                <th>Population</th>
                <th>Diner Rating</th>
            </tr>
            <tr>
                <td>Walla Walla,WA</td>
                <td>June 15th</td>
                <td>75</td>
                <td>1,204 ft</td>
                <td>29,686</td>
                <td>4/5</td>
            </tr>
            <tr>
                <td>Magic City,ID</td>
                <td>June 25th</td>
                <td>74</td>
                <td>5,312 ft</td>
                <td>50</td>
                <td>3/5</td>
            </tr>
        </table>
    </body>
    </html>
    ```
    浏览器会显示这样一个表格，见图![table1](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/table1.png)
    现在，我们来解释这段代码里的相关细节：
    1. L3-L8的首部里，是一段CSS，正是因为有这段CSS，我们才能在浏览器里看到表格的结构
    2. \<table>元素包裹整个表格
    3. \<tr>元素包裹一行，每一行一个\<tr>
    4. \<th>元素包裹一个表头，看上去好像是HTML里的一列，但是实际上我们在定义一个表头行。**浏览器默认的会使用粗体来显示表头**
    5. \<td>元素包裹一个单元格，每个单元格分别构成一个单独的列
2. **如果一行没有足够的元素，会出现什么情况？换句话说，如果实际的元素数鳌鱼表格中的列数，会有什么结果？**
    >遇到这种情况，最简单的办法是**将单元格的内容留空，即写为\<td>\</td>**。如果省去了这个单元格，表格就不能正确的排列对齐
3. 如果把表格的表头移动到表格左侧，该怎么办？
    >把表头元素放在每行的相应位置（一般是第一个）即可
4. HTML表格和CSS表格显示有什么关系？
    >HTML表格允许你使用HTML标记指定表格的结构，而CSS表格显示则提供了一种方法，可以用一种类似表格的表现形式显示块元素
5. 给表格增加一个标题
    先给出示例代码
    ```HTML
    <table>
        <caption>
        The Cities I visited on my Segway'n USA travels
        </caption>
        ·
        ·
        ·
    </table>
    ```
    标题会在表格上方显示，之后也可以用CSS调整样式，但是一些版本较老的浏览器不能完全支持标题位置的调整
6. 表格的合并行操作
    这里，先给出效果图:
    ![span two rows](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/span%20two%20rows.png)
    箭头所指的三个单元格，就是合并了两行的单元格了。对于这种情况，我们需要使用rowspan属性。下面直接来看一段代码，这比我叙述更容易理解
    ```HTML
    <tr>
        <td rowspam="2">Truth or Consequences, NM</td><!--这里我们使用rowspan属性，声明了这个单元格跨两行-->
        <td class="center">August 9th</td>
        <td class="center">93</td>
        <td rowspan="2" class="right">4,242 ft</td>
        <td rowspan="2" class+"right">7,289</td>
        <td class="center">5/5</td>
    </tr>
    <tr><!--第二列中，只指定我们需要的列-->
        <!--由于rowspan设置为2，所以不再需要城市-->
        <td class="center">August 27th</td>
        <td class="center">98</td>
        <!--同理，我们也不再需要海拔和人口-->
        <td class="center">4/5</td>
    </tr>
    ```

### 为表格增加样式
1. 为表格增加样式
    ```CSS{.line-numbers}
    table{
        margin-left: 20px;
        margin-right: 20px;
        border: thin aolid blank;
        caption-side: bottom;
    }
    td,th {
        border: thin dotted grat;
        padding: 5px;
    }
    ```
    1. L4，我们给表格加了一个黑色的细边框
    2. L5，我们把标题移动到表格下方，做成类似图注的样式
    3. L9，为单元格增加了一些内边距
2. 为标题增加样式
    ```CSS
    caption{
        font-style: italic;
        padding-top: 8px;
    }
    ```
    仅仅是修改了字体样式和增加了一些上内边距
3. 下图是增加样式后的表格![table with CSS](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/table%20with%20CSS.png)
    如果觉得表格内的双虚线很难看，只需要在table规则里增加一条`border-spacing: 0px;`即可，你也可以使用折叠边框属性`border-collapse: collapse`，这会让浏览器忽略表格上设置的所有边框间距。另外还会把紧挨着的两个边框合并为一个，这样两个边框就会“折叠”为一个边框
4. **使用伪类来使表格颜色更丰富**
    1. 什么是伪类
        >举个例子，:visited、:link、：hover都是伪类。如果一个链接被访问过，它会被浏览器丢进:visited类中，如果悬停，则是:hover。**这些就好像是类一样，浏览器会在后台自动的向这些类中增加或者删除元素，但是从来没有人在HTML中真正输入这些伪类。**
    2. 在这里我们将会用到的伪类：nth-child。我们使用它，来为某些可以统一选择的元素增加颜色
        ```CSS{.line-numbers}
        tr:nth-child(even) {
            background-color: red;
        }
        tr:nth-child(odd) {
            background-color: green;
        }
        tr:nth-child(2n) {
            background-color: red;
        }
        tr:nth-child(2n+1) {
            background-color: green;
        }
        ```
        * L1-3，L7-9，给偶数行加红色背景
        * L4-6，L10-12，给奇数行加绿色背景

### 附：为列表增加一些样式之自定义列表标记
1. Disc是默认的列表标记类型
    ```CSS
    li {
        list-style-type: disc;
    }
    ```
2. circle提供一个简单的圆形标记
    ```CSS
    li {
        list-style-type: circle;
    }
    ```
3. square提供了一个方块标记
    ```CSS
    li {
        list-style-type: square;
    }
    ```
4. none删除所有列表标记
    ```CSS
    li {
        list-style-type: none;
    }
    ```
5. 使用定制标记
    ```CSS
    li {
        list-style-image: url(images/style.png);
    }
    ```

## HTML表单
先来看看表单是如何工作的：
>1. 浏览器加载表单页面
>2. 用户输入数据并递交表单
>3. 服务器相应并且把数据交给服务器脚本处理

### 创建表单以及表单元素
1. 创建表单
    1. 示例代码如下
        ```HTML
        <form action="http://starbuzz.com/coffee.php" method="post">
            <p>Just type your name here and then click Submit <br>
            First name: <input type:"text" name="firstname" value=""> <br>
            Last name: <input type:"text" name="lastname" value=""> <br>
        <input type="Submit">
        </p>
        </form>
        ```
    2. form是如何工作的
        1. action是存放服务器脚本的URL
        2. method确定表单数据如何发送到服务器，主要由两种方法：post和get
            1. post：使用post时，所有表单数据会作为请求的一部分发送，用户不可见，当表单数据含有类似银行账户等比较私人的信息时，推荐使用post。当你的表单中含有一个\<textarea>（这是什么我们稍后会介绍），推荐你使用post，因为这个表单元素会发送大量数据
            2. get：使用get时，表单数据会追加到URL本身，所有用户可以看到表单数据。如果你希望用户能够对提交表单后的结果页面添加书签等操作，那你可以使用get。如果你有一个处理订单的服务器脚本，可能不希望用户对这个页面添加标签，否则每次用户打开这个页面时，都会重新递交这个表单。但是如果你有一个服务器脚本，它返回一个搜索结果列表，那么应该使用get，因为应该会有用户希望对这个页面添加书签
2. 表单元素
    * 文本输入
        `text <input>`元素用于输入一行文本。你还可以为这个控件设置最大字符个数和宽度
        ![text input](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/text%20input.png)
        ```HTML
        <input type="text" name="fullname">
        ```
        1. 使用type属性指示你希望得到一个文本属性的输入
        2. 使用name指定一个名字，这个名字将会交给服务器脚本进行进一步使用
        3. 使用maaxlength属性，限制最大字符长度。例：`maxlength="100"`
        4. **对于大多数\<input>控件都可以使用placeholder属性，会把它的值在控件中显示为一个颜色较浅的提示内容，而当用户单击这个文本域，提示作用的占位符就会消失，它不会和你要输入的内容混杂在一起**
            ```HTML
            <input type="text" placeholder="Buckaroo Banzai">
            ```
            ![placeholder](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/placeholder.png)
    * 递交输入
        `submit <input>`元素会创建一个按钮，允许用户递交表单。点击时，浏览器会把表单发送给服务器脚本进行处理
        ![submit input](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/submit%20input.png)
        ```HTML
        <input type="submit" value="Submit">
        ```
        1. 递交按钮需要指定"submit"作为type的值
        2. **value的值将会控制按钮上显示的文字**，这是一个可选属性，它有一个默认值"Submit"
    * 单选按钮输入
        `radio <input>`元素会创建一个包含多按钮的控件，但是一次只能选择其中一个按钮
        ```HTML
        <p>
        <input type="radio" name="hotornot" value="hot">HOT<br>
        <input type="radio" name="hotornot" value="not">NOT<br>
        </p>
        ```
        1. 使用radio属性来表示你要构建一个单选按钮
        2. 一组单选按钮将会使用同一个name
        3. value是每个按钮的值
        4. radio元素的名字都是相同的，因为我们需要让浏览器知道这些单选按钮属于同一组
        5. \<br>只是一个换行符
        6. 我们习惯把按钮的标签放在元素右边
    * 复选按钮输入
        `checkbox <input>`元素也会创建一个包含多按钮的控件，只不过是多选
        ```HTML
        <p>
        <input type="checkbox" name="hotornotorgot" value="hot" checked>HOT<br>
        <input type="checkbox" name="hotornotorgot" value="not">NOT<br>
        <input type="checkbox" name="hotornotorgot" value="got">GOT<br>
        </p>
        ```
        1. 在递交表单时，浏览器会把所以的复选按钮值联通复选按钮名发送到服务器脚本。比如在这里，假设我们选择了hot、not和got，那么浏览器会向服务器发送`"hotornotorgot=hot&not&got"`
        2. 在这个复选框内，第一个checkbox元素中有一个布尔属性：checked，它表示该项时默认选中的
    * 文本区
        `<textarea>`元素会创建一个多行的文本区，可以在其中输入多行文本
        ![textarea](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/textarea.png)
        ```HTML
        <textarea name="comments" rows="10" cols="48"></textarea>
        ```
        1. \<textare>元素不是一个空元素，它有开始和结束标记
        2. rows属性告诉浏览器，这个文本区的高度是多少个**字符**
        3. cols属性告诉浏览器，这个文本区的宽度是多少个**字符**
        4. 你也可以使用CSS来指定文本区的大小
        5. **开始和结束标记之间的文本会成为浏览器文本区控件内的初始文本**
    * select & option
        通过将这两个元素结合，可以创建一个菜单控件。菜单提供了从一组选项里选出一个的方法，见图:
        ![menu](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/menu.png)
        ```HTML
        <selecxt name="characters">
            <option value="Buckaroo">Bukaroo Banzai</option>
            <option value="Tommy">Perfect Tommy</option>
            <option value="Penny">Penny Priddy</option>
            <option value="Jersey">New Jersey</option>
            <option value="John">John Parker</option>
        </select>
        ```
        1. \<select>包含所有菜单选项，把他们组成一个菜单。和其他的表单元素一样，要使用name属性为select指定一个唯一的名字
        2. \<option>元素的内容是菜单项的描述，每个菜单选项还可以包含一个表示这个菜单项的值
        3. \<option>元素没有name属性，因为他们时菜单的一部分，而菜单由\<select>创建，所以我们只需要给整个菜单提供一个名字，而这已经在\<select>元素中指定了。递交表单时，只会把当前选择项的值连同这个名字交给服务器脚本处理
        4. 如果为\<select>元素增加一个布尔属性multiple，就会把单选菜单变成可以多选的菜单。同时，不再显示一个下拉菜单，在屏幕上显示所有选项，通过按下ctrl或者command选择多项
    * 数字输入
        `number <input>`元素会限制只能输入数字，并且可以用相关属性限制最大值和最小值
        ![number input](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/number%20input.png)
        ```HTML
        <input type="number" min="0" max="20">
        ```
        如果你输入的值超过这个范围，会得到一个错误消息
        ![error message](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/error%20message.png)
    * 范围输入
        `range <input>`元素类似于number，但是它会显示一个滑动条而不是输入框
        ![range input](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/range%20input.png)
        ```HTML
        <input type="range" min="0" max="20" step="5">
        ```
        无论是number元素还是range元素，都可以使用step来指定一个步长
    * 颜色输入
        `color <input>`元素可以指定一个颜色，单击这个控件是会弹出一个颜色选择器(如果浏览器不支持这个控件，则用户会得到一个常规的文本输入控件)
        ![color input](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/color%20input.png)
        ```HTML
        <input type="color">
        ```
    * 日期输入
        `data <input>`元素可以指定一个日期，单击这个控件时会弹出一个日历。这个控件在选择完之后会创建一个合法的日期格式串发送到服务器脚本。(如果浏览器不支持这个控件，则用户会得到一个常规的文本输入控件)
        ![date input](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/date%20input.png)
        ```HTML
        <input type="date">
        ```
    * email、tel、url输入
        `email <input>`、`tel <inpout>`、`url <input>`元素都是`text <input>`的变种，而且他们的特性在**移动设备浏览器**上才可以体现，当使用他们时，移动设备浏览器会**分别调出适合输入email或者电话号码或者url的定制键盘**
        ```HTML
        <input type="email">
        <input type="tel">
        <input type="url">
        ```
    * fieldset和legend
        这两个控件从视觉上对元素分组
        ![fieldset&legend](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/field%26legend.png)
        ```HTML
        <fieldset>
        <legend>Condiments</legend>
        <input type="checkbox" name="spice" value="salt">
        Salt <br>
        <input type="checkbox" name="spice" value="pepper">
        Pepper <br>
        <input type="checkbox" name="spice" value="garlic">
        Garlic
        </fieldset>
        ```
    * password
        这个控件会对用户输入字符加掩码
        ![password](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/password.png)
        ```HTML
        <input type="password" name="secret">
        ```
    * 文件输入
        创建一个文件选择控件，允许用户选择一个文件，并在表单递交时随其他表单数据一起发送给服务器。**使用这个控件的前提是必须使用POST方法**
        ![file input](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/file%20input.png)
        ```HTML
        <input type="file" name="doc">
        ```
    * required
        这其实是一个布尔属性，它可以用于任何表单控件，指示一个域是必要的。所以，对于设置了这个属性的控件，如果没有为这个控件指定一个值，是无法递交表单的
        ![required](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/required.png)
        ```HTML
        <input type="text" placeholder="Buckaroo Banzai" required>
        ```

### 实现表格显示布局
1. 表单通常采用表格布局，CSS表格显示布局对于显示这个表单非常合适，我们先来看将表单元素放入HTML结构中实现表格显示布局
    ```HTML{.line-numbers}
    <form action="http://starbuzzcoffee.com/processorder.php" method="post">

    <div class="tableRow"><!--使用一个类为tableRow的<div>来表示表格中的隔行-->
    <p>
    Choose your beans:
    </p>

    <p>
    <select name="beans">
    <option value="House Blend">House Blend</option>
    <option value="Bolivia">Shade Grown Bolivia Supremo</option>
    <option value="Guatemala">Organic Guatemala</option>
    <option value="Kenya">Kenya</option>
    </select>
    </p><!--选择菜单，我们把对应的所有元素放在一个单元格中-->

    </div>

    <div class="tableRow">
    <p> Type: </p><!--每个单元格的内容嵌套在一个单元格中-->

    <p>
    <input type="radio" name="beantype" value="whole"> Whole bean<br>
    <input type="radio" name="beantype" value="ground" checked> Ground
    </p><!--对于单选按钮，我们把对应的所有元素放在一个单元格中-->

    </div>

    <div class="tableRow">
    <p> Number of bags: </p>
    <p> <input type="number" name="bags" min="1" max="10"> </p>
    </div>

    <div class="tableRow label">
    <p> Must arrive by date: </p>
    <p> <input type="date" name="date"> </p>
    </div>

    <div class="tableRow">
    <p> Extras: </p>

    <p>
    <input type="checkbox" name="extras[]" value="giftwrap"> Gift wrap<br>
    <input type="checkbox" name="extras[]" value="catalog" checked>
    Include catalog with order
    </p><!--对于多选按钮，我们把对应的所有元素放在一个单元格中-->

    </div>

    <div class="tableRow">
    <p class="heading"> Ship to </p><!--对于只包含标签"ship to"的行，我们为他单独设定了一个类方便通过CSS对它字体加粗-->
    <p></p><!--注意，这里还有一个空单元格，所以在这里直接放一个空的<p>元素-->
    </div>

    <div class="tableRow">
    <p> Name: </p>
    <p> <input type="text" name="name" value=""> </p>
    </div>

    <div class="tableRow">
    <p> Address: </p>
    <p> <input type="text" name="address" value=""> </p>
    </div>

    <div class="tableRow">
    <p> City: </p>
    <p> <input type="text" name="city" value=""> </p>
    </div>

    <div class="tableRow">
    <p> State: </p>
    <p> <input type="text" name="state" value=""> </p>
    </div>

    <div class="tableRow">
    <p> Zip: </p>
    <p> <input type="text" name="zip" value=""> </p>
    </div>

    <div class="tableRow">
    <p> Phone: </p>
    <p> <input type="tel" name="phone" value=""> </p>
    </div>

    <div class="tableRow">
    <p> Customer Comments: </p>
    <p>
    <textarea name="comments" rows="10" cols="48"></textarea>
    </p>
    </div>

    <div class="tableRow">
    <p></p>
    <p> <input type="submit" value="Order Now"> </p>
    </div>

    </form>
    ```
2. 用CSS建立表单样式
    ```CSS
    body {
        background: #efe5d0 url(images/background.gif) top left;
        margin: 20px;
    }
    form {
        display: table;
        padding: 10px;
        border: thin dotted #7e7e7e;
        background-color: #e1ceb8;
    }/*在表单周围增加一个边框，在内容和边框之间增加了一些内边距，还增加了一个背景颜色*/
    form textarea {
        width: 500px;
        height: 200px;
    }/*增加表单中的textarea控件*/
    div.tableRow {
        display: table-row;
    }
    div.tableRow p {
        display: table-cell;
        vertical-align: top;
        padding: 3px;
    }/*对每个tableRow中的<p>元素设定垂直对齐，这里还增加了内边距，来增加行之间的间距*/
    div.tableRow p:first-child {
        text-align: right;
    }/*使用了first-child伪类，表示各行的第一个<p>要右对齐*/
    p.heading {
        font-weight: bold;
    }/*对heading类的<p>设置粗体*/
    ```
3. 成品表单页
    ![ready](https://raw.githubusercontent.com/shazam12c/HTML-CSSlearning/master/ready.png)

# 完结
