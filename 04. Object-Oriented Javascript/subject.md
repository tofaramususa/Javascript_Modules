# Object-Oriented JavaScript

## Working with Object Literals

### Challenge 1: Creating Objects with a Function
Create a function `makePerson` that has two parameters (`name` and `age`) and returns an object. This function will:
- Create an empty object.
- Add a `name` property to the object with its value being the `name` argument.
- Add an `age` property to the object with its value being the `age` argument.
- Return the object.

```javascript
function makePerson(name, age) {
    const person = {};
    person.name = name;
    person.age = age;
    return person;
}
```

### Challenge 2: Using `Object.create`
Inside the `personStore` object, create a property `greet` where the value is a function that logs "hello".

```javascript
const personStore = {};
personStore.greet = function() {
    console.log("hello");
};
```

### Challenge 3: Factory Function with `Object.create`
Create a function `personFromPersonStore` that takes a `name` and `age` as input. The function will:
- Use `Object.create` on the `personStore` object.
- Assign the `name` and `age` properties to the created object.
- Return the new object.

```javascript
function personFromPersonStore(name, age) {
    const person = Object.create(personStore);
    person.name = name;
    person.age = age;
    return person;
}
```

### Challenge 4: Adding Methods Without Editing Existing Code
Add an `introduce` method to the `personStore` object that logs "Hi, my name is [name]".

```javascript
personStore.introduce = function() {
    console.log(`Hi, my name is ${this.name}`);
};
```

## Using the `new` Keyword

### Challenge 5: Constructor Function with `this`
Create a function `PersonConstructor` that uses the `this` keyword to save a single property `greet`. The `greet` function logs the string "hello".

```javascript
function PersonConstructor() {
    this.greet = function() {
        console.log("hello");
    };
}
```

### Challenge 6: Factory Function with `new`
Create a function `personFromConstructor` that takes `name` and `age` as input. The function:
- Creates person objects using the `new` keyword and `PersonConstructor`.
- Assigns `name` and `age` properties to the object.

```javascript
function personFromConstructor(name, age) {
    const person = new PersonConstructor();
    person.name = name;
    person.age = age;
    return person;
}
```

### Challenge 7: Adding Methods to the Constructor Prototype
Add an `introduce` method to the `PersonConstructor` prototype that logs "Hi, my name is [name]".

```javascript
PersonConstructor.prototype.introduce = function() {
    console.log(`Hi, my name is ${this.name}`);
};
```

## Using ES6 Classes

### Challenge 8: Basic ES6 Class
Create a class `PersonClass` with:
- A constructor that takes `name` and assigns it to a property `name`.
- A `greet` method that logs "hello".

```javascript
class PersonClass {
    constructor(name) {
        this.name = name;
    }

    greet() {
        console.log("hello");
    }
}
```

### Challenge 9: Extending a Class
Create a class `DeveloperClass` that extends `PersonClass`. It should:
- Inherit the `name` property and `greet` method.
- Add an `introduce` method that logs "Hello World, my name is [name]".

```javascript
class DeveloperClass extends PersonClass {
    introduce() {
        console.log(`Hello World, my name is ${this.name}`);
    }
}
```

## Extension: Subclassing

### Challenge 10: Linking Object Methods
Create an object `adminFunctionStore` that links to all methods in the `userFunctionStore` without copying them individually.

```javascript
const adminFunctionStore = Object.create(userFunctionStore);
```

### Challenge 11: Admin Factory Function
Create an `adminFactory` function that creates objects with the same fields as `userFactory`, but without copying each field individually.

```javascript
function adminFactory() {
    const admin = Object.create(userFactory);
    admin.type = "Admin";
    return admin;
}
```

### Challenge 12: Default `type` Field for Admin Objects
Ensure `adminFactory` objects have the `type` field set to "Admin" by default.

```javascript
adminFactory.prototype.type = "Admin";
```

### Challenge 13: Linking Admin Objects to Function Store
Ensure `adminFactory` objects have access to `adminFunctionStore` methods without copying them.

```javascript
Object.setPrototypeOf(adminFactory.prototype, adminFunctionStore);
```

### Challenge 14: Adding Methods Without Direct Assignment
Create a `sharePublicMessage` method that logs "Welcome users!". This method should only be available to `adminFactory` objects.

```javascript
adminFunctionStore.sharePublicMessage = function() {
    console.log("Welcome users!");
};
```

## Extension: Mixins

### Challenge 15: Using Mixins
Assign all properties of `robotMixin` to `robotFido` in a single line without copying them individually.

```javascript
Object.assign(robotFido, robotMixin);
