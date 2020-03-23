title: This
author: zhangjingjie
date: 2020-03-24 01:04:13
tags:
---
**this** 关键字是 JavaScript 中最复杂的机制之一 ,在理解 **this** 之前先理解一段这个代码
```javascprit
var a = 1
function foo (){
	var a = 2;
    bar();
};
function bar(){
	console.log(a);
};

foo()
```
答案是 1. 为什么呢？ 因为词法作用域的关系也可以理解成为静态作用域。
事实上很多语言都是基于词法作用域的,但是Javascript并不是完全的静态作用域 **This**就是为了实现动态作用域的一个重要机制
```javascprit
function foo(){return this.name}
var name = 'foo';
var obj = { name:'baz',foo}
foo();
obj.foo();
```
得到结果是 foo 和 baz 通过使用 **this** 来更优雅的方式来隐式传递一个对象的引用, 很容易把this理解成为函数的自身。从翻译的角度来这个没并有错，但这并不是正确的理解。 

前面说过**this是实现动态作用域的一个重要机制**，所以this是在**运行时**进行绑定的,而不是在编写时绑定的。它的上下文取决于函数调用的各种条件。this的绑定和声明函数的位置没有关系，它取决于函数在哪里被调用。