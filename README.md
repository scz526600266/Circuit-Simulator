# 在线电路仿真

[电路仿真 (Circuit Simulator)](https://xiaoboost.github.io/Circuit-Simulator/)  
这是个在线的电路图绘制网站，完整的实现了电路图的绘制以及时域部分仿真。 

## 相关说明
`vue`重构的分支。
**！！未完成！！** 

## 操作及说明

### 运行设置
在`运行设置`界面中有两个输入项：`计算步长`以及`终止时间`。
计算步长就是每次方程迭代的间隔时间，这里的时间并不是现实时间，而是仿真的时间，终止时间自然就是仿真的总时长。  
理论上间隔时间越小仿真结果就越精确，我建议计算步长至少都要是终止时间的千分之一。  

### 器件操作
在`添加器件`界面，单击你想要添加的器件就可以了，移动鼠标到图中，然后再次单击就会放下器件。  
在图纸中空白部分点击左键并按住不放，此时移动鼠标可以选择多个器件。  
器件移动只会影响器件和导线的位置和路径，所有的连接关系都不会发生改变。  

### 器件属性
对器件双击左键或者点击右键相关选项，都可以修改器件属性。  
器件属性包含它本身的ID以及相关属性。  
器件的合法ID的格式是`英文 + 下划线 + 英文或者数字`。  
器件ID对外显示将会省略下划线，而且下划线之后的字符串将会成为前面的下标。  
器件的相关属性中，只允许使用数字以及以下缩写：`G`、`M`、`k`、`m`、`u`、`n`、`p`。  
输入非法ID或属性值，都将禁止你离开当前界面，除非你点击取消或者将其修改正确。  
在修改器件对话框中，允许使用键盘`Esc`和`Enter`键，它们分别代表`取消`和`确认`。  

### 导线绘制
对器件任意空白引脚点击左键并按住不放，此时就可以绘制导线，再松开鼠标就表示绘制完成。  
对器件任意已连接导线的引脚点击左键并按住不放，此时将会断开此器件与此导线的连接，并重绘当前导线。  
对多个导线的连接点点击左键并按住不放，也将会断开当前方向上导线与其余导线的连接，并重绘当前导线。  
对导线的某一段点击左键并按住不放，此时可以直接对导线进行变形。  

### 波形显示栏
仿真结果将会分为两栏，`电压`和`电流`，所有的电压结果都会放到同一栏中，电流也是一样，现在还不支持自定义分栏。  
在波形显示框中点击左键并按住不放，可以自由选择显示范围。再点击左上角的`取消缩放`按钮，波形将恢复原状。  
在右上角有波形颜色相关的图示，对波形名字点击左键，就可以隐藏它的波形，再次点击就会恢复。  

### 其他
在图纸中空白部分点击鼠标右键并按住不放，此时移动鼠标可以移动图纸。  
在没有进行导线绘制、器件移动、新建器件操作时，滚动鼠标滚轮可以放大和缩小图纸。  

## 器件说明
由于求解器的效率问题，现在所有器件均采用理想数学模型。  
具体而言就是，二极管、三极管都是分段函数，运放是无穷带宽。  
在求解器的效率问题解决之后，会更新它们的非理想建模。  

## 几个实例 
[直流电源的一阶零状态响应](https://xiaoboost.github.io/Circuit-Simulator/?init=FirstOrderCircuitDC)  
[交流电源的一阶零状态响应](https://xiaoboost.github.io/Circuit-Simulator/?init=FirstOrderCircuitAC)  
[桥式整流电路](https://xiaoboost.github.io/Circuit-Simulator/?init=BridgeRectifier)  
[运放的同相放大](https://xiaoboost.github.io/Circuit-Simulator/?init=PhaseAmplifier)  
[三极管共射放大](https://xiaoboost.github.io/Circuit-Simulator/?init=CommonEmitterAmplifier)  
[三极管射极跟随](https://xiaoboost.github.io/Circuit-Simulator/?init=EmitterFollower)

## 浏览器支持
Chrome 42+  

## 注意
Chrome的页面放大有Bug，在页面缩放比例不是100%的时候，背景网格会对不齐。

## 许可
MIT License
