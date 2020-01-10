JavaScript Questions

## Undefined Vs Not Defined
var x; 
console.log(x) // x is undefined.
console.log(y) // y is not defined.

## Drawback of declaring methods directly in JavaScript objects?
They are very memory inefficient. When you do that, a new copy of the method is created for each instance of an object.

## What is “closure” in javascript? Can you provide an example?
A closure is a function defined inside another function (called parent function) and has access to the variable which is declared and defined in parent function scope.
The closure has access to the variable in three scopes:
* Variable declared in his own scope
* Variable declared in parent function scope
* Variable declared in the global namespace

## Write a mul function which will work properly when invoked with following syntax.
function mul (x) {
  return function (y) { // anonymous function
    return function (z) { // anonymous function
      return x * y * z;
    };
  };
}

## How to empty an array in JavaScript?
// 1
arrayList = [];
// 2
arrayList.length = 0;
//3
arrayList.splice(0, arrayList.length);
//4
while(arrayList.length) {
  arrayList.pop();
}

## How to check if an object is an array or not?
if(Object.prototype.toString.call(arrayList) === '[object Array]') {
  console.log('Array!');
}

## What will be the output of the following code?
```
var x = 1;
var output = (function() {
  delete x;
  return x;
})();

console.log(output);
```
The code above will output 1 as output. delete operator is used to delete a property from an object. Here x is not an object it's global variable of type number.

## What will be the output of the following code?
```
var Employee = {
  company: 'xyz'
}
var emp1 = Object.create(Employee);
delete emp1.company
console.log(emp1.company);
```
The code above will output xyz as output. Here emp1 object got company as prototype property. delete operator doesn't delete prototype property.

## What will be the output of the following code?
```
var trees = ["xyz", "xxxx", "test", "ryan", "apple"];
delete trees[3];
console.log(trees.length);
```
The code above will output 5 as output. When we used delete operator for deleting an array element then, the array length is not affected by this. This holds even if you deleted all elements of an array using delete operator.

## What will be the output of the following code?
```
var bar = true;
console.log(bar + 0);   
console.log(bar + "xyz");  
console.log(bar + true);  
console.log(bar + false);
```
The code above will output 1, "truexyz", 2, 1 as output. Here's a general guideline for the plus operator:
* Number + Number -> Addition
* Boolean + Number -> Addition
* Boolean + Boolean -> Addition
* Number + String -> Concatenation
* String + Boolean -> Concatenation
* String + String -> Concatenation

## What will be the output of the following code?
```
var z = 1, y = z = typeof y;
console.log(y);
```
Output: undefined

## What is the difference between declaring a function in the formats listed below?
```
var foo = function() {
  // Some code
}

function bar () {
  // Some code
}
```
The main difference is that function foo is defined at run-time and is called a function expression, whereas function bar is defined at parse time and is called a function statement.


## What will be the output of the following code?
```
var salary = "1000$";

(function () {
  console.log("Original salary was " + salary);

  var salary = "5000$";

  console.log("My New Salary " + salary);
})();
```
The code above will output: undefined, 5000$ because of hoisting. In the code presented above, you might be expecting salary to retain it values from outer scope until the point that salary was re-declared in the inner scope. But due to hoisting salary value was undefined instead.

## What’s the difference between typeof and instanceof?
typeof is an operator that returns a string with the type of whatever you pass.
The typeof operator checks if a value belongs to one of the seven basic types: number, string, boolean, object, function, undefined or Symbol.
instanceof is much more intelligent: it works on the level of prototypes. In particular, it tests to see if the right operand appears anywhere in the prototype chain of the left.

## Calculate the length of the associative array
```
var counterArray = {
  A : 3,
  B : 4
};
counterArray["C"] = 1;
```
// 1
Object.keys(counterArray).length;
// 2
```
function getLength(object) {
  var count = 0;
  for(key in object) {
    // hasOwnProperty method check own property of object
    if(object.hasOwnProperty(key)) count++;
  }
  return count;
}
```
// 3
Object.getOwnPropertyNames(counterArray).length; // Output 3

## Difference between Function, Method and Constructor calls in JavaScript.
// function
function helloWorld(name) {
  return "hello world, " + name;
}
// method
var obj = {
  helloWorld : function() {
    return "hello world, " + this.name;
  },
  name: 'John Carter'
}
// constructor
function Employee(name, age) {
  this.name = name;
  this.age = age;
}

## What are Service Workers and when can you use them?
It’s a technology that allows your web application to use cached resources first, and provide default experience offline, before getting more data from the network later. This principle is commonly known as Offline First.

Service Workers actively use promises. A Service Worker has to be installed,activated and then it can react on fetch, push and sync events.

## What is IIFE (Immediately Invoked Function Expression) and how it can be useful?
IIFE a function that runs as soon as it's defined. Usually it's anonymous (doesn't have a function name), but it also can be named. Here's an example of IIFE:
So, here's how it works. Remember the difference between function statements (function a () {}) and function expressions (var a = function() {})? So, IIFE is a function expression. To make it an expression we surround our function declaration into the parens. We do it to explicitly tell the parser that it's an expression, not a statement (JS doesn't allow statements in parens).

After the function you can see the two () braces, this is how we run the function we just declared.

## Describe Singleton Pattern In JavaScript
The singleton pattern is an often used JavaScript design pattern. It provides a way to wrap the code into a logical unit that can be accessed through a single variable. The Singleton design pattern is used when only one instance of an object is needed throughout the lifetime of an application. In JavaScript, Singleton pattern have many uses, they can be used for NameSpacing, which reduce the number of global variables in your page (prevent from polluting global space), organizing the code in a consistent manner, which increase the readability and maintainability of your pages.

There are two important points in the traditional definition of Singleton pattern:
* There should be only one instance allowed for a class and
* We should allow global point of access to that single instance

## What are promises and how they are useful?

We use promises for handling asynchronous interactions in a sequential manner. They are especially useful when we need to do an async operation and THEN do another async operation based on the results of the first one. For example, if you want to request the list of all flights and then for each flight you want to request some details about it. The promise represents the future value. It has an internal state (pending, fulfilled and rejected) and works like a state machine.

A promise object has then method, where you can specify what to do when the promise is fulfilled or rejected.

You can chain then() blocks, thus avoiding the callback hell. You can handle errors in the catch() block. After a promise is set to fulfilled or rejected state, it becomes immutable.

## What is NaN, why do we need it, and when can it break the page?
NaN stands for “not a number.” and it can break your table of numbers when it has an arithmetic operation that is not allowed.

## How we can prevent modification of object in JavaScript ?.
1: Prevent extensions :
```
var employee = {
  name: "Nishant"
};

// lock the object 
Object.preventExtensions(employee);

// Now try to change the employee object property name
employee.name = "John"; // work fine 

//Now try to add some new property to the object
employee.age = 24; // fails silently unless it's inside the strict mode
```
2: Seal :
```
var employee = {
  name: "Nishant"
};

// Seal the object 
Object.seal(employee);

console.log(Object.isExtensible(employee)); // false
console.log(Object.isSealed(employee)); // true

delete employee.name // fails silently unless it's in strict mode

// Trying to add new property will give an error
employee.age = 30; // fails silently unless in strict mode
```
3: Freeze 
```
var employee = {
  name: "Nishant"
};

//Freeze the object
Object.freeze(employee); 

// Seal the object 
Object.seal(employee);

console.log(Object.isExtensible(employee)); // false
console.log(Object.isSealed(employee));     // true
console.log(Object.isFrozen(employee));     // true


employee.name = "xyz"; // fails silently unless in strict mode
employee.age = 30;     // fails silently unless in strict mode
delete employee.name   // fails silently unless it's in strict mode
```
