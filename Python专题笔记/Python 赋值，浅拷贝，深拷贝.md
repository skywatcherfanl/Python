Python 赋值，浅拷贝，深拷贝
=========================

> 直接赋值：对象的引用（别名）。    
> 浅拷贝(copy)：拷贝父对象，不会拷贝对象的内部的子对象。    
> 深拷贝(deepcopy)： copy模块的deepcopy方法，完全拷贝了父对象及其子对象。    

# 1 基础概念

在Python里，一切皆对象，完全的面向对象。  
1、Python为动态解释性语言，在赋值操作时，并不需要像静态编译类型语言C++或Java一样，在使用变量前，需声明变量的类型。在Python中，类型是在运行过程中自动决定的，而不是通过代码声明。这意味着没有必要事先声明变量。   
2、变量和对象之间的关系为引用。  

## 1.1 变量

1、第一次赋值时，即创建它，之后赋值将会改变变量的值。   
2、变量名本身是没有类型的，类型只存在对象中，变量只是引用了对象而已。  
3、所有的变量，在使用前必须赋值，使用未赋值的变量会产生错误。  

## 1.2 对象

1、对象是有类型的。  
2、对象是分配的一块内存空间，来表示它的值。  
3、每一个对象都具有两个标准的头部信息。类型标志符，标识对象的类型。引用计数器，用来决定对象是不是进行回收。

### Python对象三要素：Id，Type，Value
<div align=center>
<img width="500" src="img/1.1.jpg"/>
</div>
<div align=center>图1.1 对象三要素</div>

> Id：唯一标识一个对象   
> Type：标识对象的类型    
> Value：对象的值  

a is b 判断 a 对象是否就是 b 对象（通过id来判断）   
a == b 判断 a 对象的值是否和 b 对象的值相等（通过value来判断）   

### 可变对象与不可变对象
Python的对象分成两类：可变对象和不可变对象。所谓可变对象是指，对象的内容是可变的，一般是指引用类型。而不可变的对象则相反，表示其内容不可变。对于tuple中的可变对象也是可以改变的。
> 不可变对象 ：int, float, complex, str,bool, tuple, frozenset    
> 可变对象   ：list, dict, set



## 1.3 引用

1、在Python中从变量到对象的连接称作引用。  
2、引用是一种关系，以内存中的指针的形式实现。  
3、赋值操作时，自动建立变量和对象之间的关系，即引用。  

# 2 赋值和引用
在python中赋值语句总是建立对象的引用值，而不是复制对象。因此，python变量更像是指针，而不是数据存储区域。

``` python
a = 3
b = a
```
a 指向对象3; b = a,此赋值操作，b也指向3。   
<div align=center>
<img width="450" src="img/2.2.PNG"/>
</div>
<div align=center>图2.1 赋值与引用</div>

可以看出，a和b都引用了同一个对象。

``` python
a = 3
b = a
a = 'spam'
```
<div align=center>
<img width="400" src="img/2.3.PNG"/>
</div>
<div align=center>图2.2 变量修改</div>

Python 中的赋值语句不会创建对象的拷贝，仅仅只是将名称绑定至一个对象。对于不可变对象，通常没什么差别，但是处理可变对象或可变对象的集合时，你可能需要创建这些对象的 “真实拷贝”，也就是在修改创建的拷贝时不改变原始的对象。

# 3 浅拷贝和深拷贝

浅拷贝：浅拷贝意味着构造一个新的集合对象，然后用原始对象中找到的子对象的引用来填充它。从本质上讲，浅层的复制只有一层的深度。复制过程不会递归，因此不会创建子对象本身的副本。    
深拷贝：深拷贝使复制过程递归。这意味着首先构造一个新的集合对象，然后递归地用在原始对象中找到的子对象的副本填充它。以这种方式复制一个对象，遍历整个对象树，以创建原始对象及其所有子对象的完全独立的克隆。    
## 3.1 赋值引用 
b = a，a 和 b 都指向同一个对象。
<div align=center>
<img width="400" src="img/3.1.png"/>
</div>
<div align=center>图3.1 赋值</div>


## 3.2 浅拷贝 
b = a.copy(), a 和 b 是一个独立的对象，但他们的子对象还是指向统一对象（是引用）。
<div align=center>
<img width="400" src="img/3.2.png"/>
</div>
<div align=center>图3.2 浅拷贝</div> 

## 3.3 深度拷贝 
b = copy.deepcopy(a), a 和 b 完全拷贝了父对象及其子对象，两者是完全独立的。
<div align=center>
<img width="400" src="img/3.3.png"/>
</div>
<div align=center>图3.3 深拷贝</div>

-----------
> [Python3学习笔记：Python中的赋值操作](https://blog.csdn.net/DFIE1234/article/details/86477311?utm_source=distribute.pc_relevant.none-task)    
> [Python 直接赋值、浅拷贝和深度拷贝解析](https://www.runoob.com/w3cnote/python-understanding-dict-copy-shallow-or-deep.html)
