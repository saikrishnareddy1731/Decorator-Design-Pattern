# Decorator Design Pattern in Java

## Overview

The **Decorator Pattern** is a **structural design pattern** that allows you to dynamically add behavior to an object at runtime without affecting other instances of the same class. It provides a flexible alternative to inheritance for extending functionality.

### Key Points

- Decorates objects by wrapping them in other objects.
- Each object can have **its behavior changed independently**.
- Unlike inheritance, which adds functionality at **compile time**, decorators allow **runtime modifications**.
- Can lead to complex stacks of wrappers if overused.

### Real-world Examples

- **Customized Pizza:** Base pizza + different toppings like cheese, cheese burst, jalapeno, etc.
- **Bank Accounts:** Base `Account` decorated with features like salary account benefits or preferred account perks.
- **Java API:** `Collections.unmodifiableMap()` decorates a map to make it unmodifiable.

---

## Components of Decorator Pattern

1. **Interface:** Base product definition (e.g., `Pizza`).
2. **Concrete Component:** Base implementation (e.g., `BasePizza`).
3. **Abstract Decorator:** Holds a reference to the product and implements the interface.
4. **Concrete Decorators:** Extend the abstract decorator and add new behavior (e.g., `CheeseBurstDecorator`, `JalepanoDecorator`).

---

## How It Works

- Start with a **base object**.
- Wrap it with **one or more decorators**, each adding its behavior.
- Each decorator delegates to the wrapped object and enhances its behavior.
- Final object combines all behaviors in a **dynamic chain**.

**Example Concept:**  
`BasePizza` → `CheeseBurstDecorator` → `JalepanoDecorator` → Final baked pizza with cheese and jalapeno.

---

## Advantages

- Adds functionality dynamically without altering existing code.
- More flexible than inheritance.
- Follows **Open/Closed Principle** — open for extension, closed for modification.

## Disadvantages

- Can create **complex chains of decorators**.
- Debugging becomes harder with many layers.

---

## References

- [Java Design Patterns – Decorator](https://www.javadevjournal.com/java-design-patterns/decorator-design-pattern/)
- [Decorator Pattern Paper](https://cecs.wright.edu/~tkprasad/courses/ceg860/paper/node26.html)


## UML Diagram

```mermaid
classDiagram
    direction LR

    Pizza <|.. BasePizza
    Pizza <|.. PizzaDecorator
    PizzaDecorator <|-- CheeseBurstDecorator
    PizzaDecorator <|-- JalepanoDecorator

    class Pizza {
        +bake(): String
    }

    class BasePizza {
        +bake(): String
    }

    class PizzaDecorator {
        -pizza: Pizza
        +PizzaDecorator(pizza: Pizza)
        +bake(): String
    }

    class CheeseBurstDecorator {
        +bake(): String
        +addCheese(): String
    }

    class JalepanoDecorator {
        +bake(): String
        +addJalepano(): String
    }

    PizzaDecorator --> Pizza : wraps
