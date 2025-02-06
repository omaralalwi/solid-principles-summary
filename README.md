# SOLID Principles Summary

## Introduction

The SOLID principles are a set of five design principles intended to make software designs more understandable, flexible, and maintainable. Introduced by Robert C. Martin (also known as Uncle Bob), these principles are essential for creating robust and scalable software systems.

## Table of Contents

1. [Single Responsibility Principle (SRP)](#single-responsibility-principle-srp)
2. [Open-Closed Principle (OCP)](#open-closed-principle-ocp)
3. [Liskov Substitution Principle (LSP)](#liskov-substitution-principle-lsp)
4. [Interface Segregation Principle (ISP)](#interface-segregation-principle-isp)
5. [Dependency Inversion Principle (DIP)](#dependency-inversion-principle-dip)
6. [Conclusion](#conclusion)

---

## Single Responsibility Principle (SRP)

### Definition

> A class should have only one reason to change.

### Explanation

The Single Responsibility Principle states that every class or module in a program should have responsibility over a single part of the program's functionality. This means that a class should not take on multiple responsibilities, as this can lead to a higher risk of bugs and decreased maintainability.

### Example

Consider a `User` class that handles user data and also manages user notifications. To adhere to SRP, you should separate these responsibilities into different classes, such as `User` and `NotificationService`.

```php
<?php
class User {
    private $name;
    private $email;

    public function __construct($name, $email) {
        $this->name = $name;
        $this->email = $email;
    }

    // User-related methods
}

class NotificationService {
    public function sendNotification(User $user, $message) {
        // Send notification logic
    }
}

```

---

## Open-Closed Principle (OCP)

### Definition

> Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.

### Explanation

The Open-Closed Principle suggests that you should design your modules, classes, and functions in a way that allows you to extend their behavior without modifying their source code. This can be achieved through inheritance, interfaces, and abstract classes.

### Example

Suppose you have a `Shape` class with a `draw` method. To add a new shape without modifying the existing code, you can create a new class that implements the `Shape` interface.

```php
<?php
interface Shape {
    public function draw();
}

class Circle implements Shape {
    public function draw() {
        // Draw circle logic
    }
}

class Square implements Shape {
    public function draw() {
        // Draw square logic
    }
}
```

---

## Liskov Substitution Principle (LSP)

### Definition

> Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it.

### Explanation

The Liskov Substitution Principle states that objects of a superclass should be replaceable with objects of its subclasses without affecting the correctness of the program. This means that subclasses should maintain the behavior expected by the superclass.

### Example

If you have a `Bird` class with a `fly` method, a `Penguin` subclass should not inherit from `Bird` because penguins cannot fly. Instead, you might have a `FlyingBird` class and a `Bird` class without the `fly` method.

```php
<?php
class Bird {
    public function speak() {
        // Speak logic
    }
}

class FlyingBird extends Bird {
    public function fly() {
        // Fly logic
    }
}

class Penguin extends Bird {
    public function swim() {
        // Swim logic
    }
}
```

---

## Interface Segregation Principle (ISP)

### Definition

> No client should be forced to depend on methods it does not use.

### Explanation

The Interface Segregation Principle suggests that you should create specific interfaces for each client, rather than one general-purpose interface. This prevents clients from having to implement methods they do not need.

### Example

Instead of having a single `Worker` interface with `work` and `eat` methods, you can split it into `Workable` and `Eatable` interfaces.

```php
<?php
interface Workable {
    public function work();
}

interface Eatable {
    public function eat();
}

class Human implements Workable, Eatable {
    public function work() {
        // Work logic
    }

    public function eat() {
        // Eat logic
    }
}

class Robot implements Workable {
    public function work() {
        // Work logic
    }
}
```

---

## Dependency Inversion Principle (DIP)

### Definition

> High-level modules should not depend on low-level modules. Both should depend on abstractions.

### Explanation

The Dependency Inversion Principle states that high-level modules should not depend on low-level modules. Instead, both should depend on abstractions. This can be achieved through the use of interfaces and dependency injection.

### Example

Instead of having a `Car` class depend directly on a `Engine` class, you can have the `Car` class depend on an `Engine` interface.

```php
<?php
interface Engine {
    public function start();
}

class ElectricEngine implements Engine {
    public function start() {
        // Start electric engine logic
    }
}

class Car {
    private $engine;

    public function __construct(Engine $engine) {
        $this->engine = $engine;
    }

    public function start() {
        $this->engine->start();
    }
}
```

---

## Conclusion

The SOLID principles provide a framework for creating software that is modular, maintainable, and scalable. By adhering to these principles, developers can design systems that are easier to understand, test, and extend.

### References

- [SOLID Principles - Wikipedia](https://en.wikipedia.org/wiki/SOLID)
- [Clean Code by Robert C. Martin](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)

## Helpful Links

- [Clean Code Summary](https://github.com/omaralalwi/clean-code-summary)
