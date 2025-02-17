# 网页特效

## 元素偏移量 offset 系列

offset 翻译过来就是偏移量，我们使用offset系列相关属性可以**动态的**得到该元素的位置（偏移）、大小等。

- 获得元素距离带有定位父元素的位置
- 可以获取元素自身的宽度和高度
- 注意：返回的数值不带单位

offset 系列常用属性:

| offset 系列属性      | 作用                                                         |
| -------------------- | ------------------------------------------------------------ |
| element.offsetParent | 返回作为该元素带有定位的父级元素如果父级都没有定位则返回body |
| element.offsetTop    | 返回元素相对带有定位父元素上方的偏移                         |
| element.offsetLeft   | 返回元素相对带有定位父元素左边框的偏移                       |
| element.offsetWidth  | 返回自身包括padding、边框、内容区的宽度，返回数值不带单位    |
| element.offsetHeight | 返回自身包括padding、边框、内容区的高度，返回数值不带单位    |

### offset 和 style 区别

| offset      | style                                                         |
| -------------------- | ------------------------------------------------------------ |
| offset 可以得到任意样式表中的样式值 | style 只能得到行内样式表中的样式值 |
| offset 系列获得的数值没有单位    | style.width 获得的是带有单位的字符串           |
| offsetWidth 包含 padding + border + width   | style.width 获得不包括padding + border的值    |
| offsetWidth 等属性是只读属性，只能获取不能修改  | style.width 是可读写属性，可以获取也可以赋值  |
| 我们想要获取元素的大小位置，用 offset 更合适 |想要给元素更改值，用style 改变    |

### 案例：获取鼠标在盒子里的位置

#### 案例分析：

- 我们在盒子里面移动鼠标，想要获取鼠标距离盒子左边和上面的距离
- 首先得到鼠标在页面中的坐标（ｅ．ｐａｇｅＸ　和　ｅ．ｐａｇｅＹ）
- 其次得到盒子在页面中的距离（ｂｏｘ．ｏｆｆｓｅｔＬｅｆｔ　和　ｂｏｘ．ｏｆｆｓｅｔＴｏｐ）
- 用鼠标距离页面的坐标减去盒子和页面边框的距离，就是鼠标在盒子里的坐标

```html
<div class="box"></div>
<script>
    var box = document.querySelector('.box');
    box.addEventListener('mousemove', function(e) {
        var x = e.pageX - this.offsetLeft;
        var y = e.pageY - this.offsetTop;
        box.innerHTML = ('X坐标是' + x + '；Y坐标是' + y);
    });
</script>
```

### 案例：拖动模态框

#### 案例分析：

- 点击弹出层，会弹出模态框，并且显示灰色半透明测遮挡层
- 点击关闭按钮，可以关闭模态框，并且同时关闭灰色半透明遮挡层
- 鼠标放到模态框最上面一行，可以按住鼠标拖动模态框在页面中移动
- 鼠标松开，模态框停止移动













更新到p101