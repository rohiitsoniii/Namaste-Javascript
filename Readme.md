

# JavaScript Code Execution: Behind the Scenes

Understanding how JavaScript code runs is crucial for mastering the language. Below is a breakdown of the key concepts involved in JavaScript execution:

## 1. Execution Context
An **Execution Context** is the environment where JavaScript code runs. There are two main types:
- **Global Execution Context (GEC)**: Created when the script first executes. Handles non-function code.
- **Function Execution Context (FEC)**: Created whenever a function is invoked.

Each context goes through two phases:
- **Creation Phase**: Memory is allocated for variables (set to `undefined`) and functions (defined with their entire code).
- **Execution Phase**: Code runs line by line, assigning actual values to variables.

The execution context has:
- **Variable Environment**: Stores variables and function declarations.
- **Lexical Environment**: Includes the current context and its outer scope.
- **`this` Binding**: Represents the value of `this` within the context (e.g., in the global context, `this` refers to `window` in browsers).

## 2. Call Stack
The **Call Stack** tracks function calls:
- Global Execution Context is pushed to the stack first.
- Function calls push their respective contexts to the stack.
- Once a function completes, its context is popped off the stack.

**Example:**
```js
function a() {
  console.log("Inside a");
  b();
}

function b() {
  console.log("Inside b");
}

a();
```

## 3. Memory Heap
The **Memory Heap** is where objects, arrays, and functions are stored. It's an unstructured area of memory used for dynamic memory allocation.

## 4. Event Loop and Callback Queue
JavaScript uses an **Event Loop** to handle asynchronous code despite being single-threaded. The **Call Stack** runs synchronous code, while the **Callback Queue** holds asynchronous tasks (e.g., `setTimeout`, `fetch`) to be executed when the stack is empty.

**Example:**
```js
console.log('Start');
setTimeout(() => console.log('Inside timeout'), 1000);
console.log('End');
```

## 5. Hoisting
Variables and functions are **hoisted** during the creation phase, meaning their declarations are moved to the top of their scope. However, variables declared with `var` are initialized as `undefined`.

**Example:**
```js
console.log(a); // undefined
var a = 5;
```

## 6. Lexical Environment and Scope Chain
Each execution context has a **Lexical Environment** that defines the scope of variables. It includes references to its parent context, creating a **Scope Chain** that determines where variables can be accessed.

- **Global Scope**: Accessible everywhere.
- **Function Scope**: Accessible only inside functions.
- **Block Scope**: Variables declared with `let` or `const` are block-scoped.

## 7. Closures
A **Closure** occurs when a function "remembers" its lexical environment even when called outside its original context.

**Example:**
```js
function outer() {
  var a = 10;
  return function inner() {
    console.log(a);
  };
}

var closureFunc = outer();
closureFunc(); // Outputs: 10
```

## Summary
- **Execution Context**: Manages variable initialization and code execution.
- **Call Stack**: Tracks function calls.
- **Memory Heap**: Stores dynamic data.
- **Event Loop**: Manages asynchronous operations.
- **Hoisting**: Moves variable and function declarations to the top.
- **Lexical Environment**: Manages scope and access to variables.
- **Closures**: Functions retain access to outer variables even after the outer function has finished.

---
