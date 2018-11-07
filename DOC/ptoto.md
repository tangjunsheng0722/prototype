# 原型链
## 原型的含义
> 在JavaScript中原型是一个prototype对象，用于表示类型之间的关系
## 原型链的含义
> 原型链是针对构造函数的，比如我先创建了一个函数，然后通过一个变量new了这个函数，那么这个被new出来的函数就会继承创建出来的那个函数的属性，然后如果我访问new出来的这个函数的某个属性，但是我并没有在这个new出来的函数中定义这个变量，那么它就会往上（向创建出它的函数中）查找，这个查找的过程就叫做原型链。
## 构造函数
> 创建一个构造函数
```
function Person(){
    name : 'aa',
    age : 22,
    sayName ：function(){
        alert(this.name)
    }
}
```
## 实例化一个构造函数
```
var person1 = new Person();
```
>实例是通过构造函数创建的。实例一创造出来就具有constructor属性（指向构造函数）和proto属性（指向原型对象）
```
person1.constructor == Person;
person1.__proto__ == Person.prototype
```
## 原型继承
>基本思想就是利用原型让一个引用类型继承另一个引用类型的属性和方法
```
// 因为Person中有person1指定且没有的sayName和name，所以继承了Person的sayName()  name
 person1.sayName();  //  'aa';
```
## 原型链
> 上例中person1.--proto-- 指向 Person.prototype,如果person1中找不到你所指定的属性或者方法，就会查找Person.prototype,如果还没有就会查找Person的构造函数的prototype，直到找到为止或者找到null; 这样就形成了一条原型链。


```
var A = function(){};
var a = new A();
// a.__proto__ == A.prototype;
   a.__proto__.__proto__ == A.__proto__ == Object.prototype;
   a.__proto__.__proto__.__proto__== A.__proto__.__proto__ == Object.--proto-- == null;
```
> 这样就形成了一条原型链

