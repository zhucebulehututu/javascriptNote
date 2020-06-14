# js基础

## 1.this指向问题

一般this指的的调用函数的那个对象。不同的场景this的指向会有变化：

1. 如果是一般函数，this指向全局对象window
2. 在严格模式下'user strict' 为undefined
3. 对象的方法里调用，this指向该方法的对象
4. 构造函数里的this，指向new 出来的实例
5. 通过事件绑定的方法，this 指向绑定事件的对象
6. 定时器函数里的this 指向window

## 2.修改this指向的三个方法

* call(thisObj,val1,val2,val3...)
* apply(thisObj,[argArray])
* bind(thisArg)

## 3. call 和 apply的区别

* 相同点：
都是为了用一个本不属于一个对象的方法，让这个对象去执行

* 区别

call() 方法第一个参数是函数运行的作用域（this的指向），第二个参数开始是传递给函数的参数
apply() 方法接收两个参数，第一个和call一样是this的指向的作用域，第二个参数一个数组或者类数组用来存放传递给函数的参数

* 说明

如果thisArg是null或者undefined，默认指向window
如果argArray不是一个有效数组或不是arguments对象,那么将导致一个TypeError，如果没有提供argArray和thisObj任何一个参数，那么Global对象将用作thisObj
call方法可以用来替代另一个对象的一个方法，call方法可以将一个函数的对象上下文从初始的上下文改变为thisObj指定的新对象，如果没有提供thisObj参数，那么Global对象被用于thisObj

## 4.bind

能够返回一个新的函数，新的函数的主体和原函数主体一致，但当新函数被调用执行时，函数体中的this指向的是thisArg所表示的对象

区别：

返回值的区别：
bind的返回值是一个函数，而call和apply是立即调用

参数使用的区别：
bind 和call一样是从第二个参数开始将想要传递的参数一一写入，但call是把第二及以后的参数作为fn方法的实参传进去，而fn1方法的实参实则是在bind中参数的基础上在往后排

## 5.闭包

闭包函数：声明在一个函数中的函数，叫做比较函数

闭包：是指有权访问另外一个函数作用域中的变量的函数。可以理解为能够读取另一个函数作用域的变量的函数

闭包一般发生在函数套函数的时候，当一个函数执行完毕之后，正常会被垃圾回收，但是执行完后，没有被回收依然被外部变量所调用的时候，这时候就形成了闭包