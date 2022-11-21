---
layout: post
title:  "What difference between switch/case and pattern matching?"
date:   2022-11-20 23:33:27 -0400
categories: programming-language
---

## Switch/Case

The switch/case just checks the equality of the values.

```js
const f = (x) => {
  if (x === 1) {
    console.log('Number 1');
  } else {
    console.log(`Number ${x}`);
  }
};
```

We can note that the code above is equivalent to the below code.

```js
const f = (x) => {
  switch (x) {
    case 1:
      console.log('Number 1');
      break;
    default:
      console.log(`Number ${x}`);
      break;
  }
};
```

Both codes just check if the value `x` is equal to 1.

## Pattern Matching

While pattern matching has exhaustive checks (in programming languages typed) and nesting.

#### Exhaustive check

For example, we have the following data constructor:

```hs
data Color
  = Red
  | Green
  | Blue
```

And we want to do a function for printing these constructors.

```hs
printColor :: Color -> IO ()
printColor color =
  case color of
    Red -> putStrLn "Red"
    Green -> putStrLn "Green"
```

We forgot the `Green` pattern.

<img width="800" alt="image" src="https://user-images.githubusercontent.com/44513615/202954800-f8c59e3d-6790-4dd4-8483-79f06106e0df.png">

The exhaustive checker, check if is missing some pattern. This avoids throwing errors in runtime.

#### Nesting

Nesting allows you get patterns into patterns, like this:

```hs
data Nat
  = Z
  | S Nat
  deriving (Show)

even :: Nat -> Bool
even Z = True
even (S Z) = False
even (S (S Z)) = True
even (S (S (S n))) = even (S n)
```
