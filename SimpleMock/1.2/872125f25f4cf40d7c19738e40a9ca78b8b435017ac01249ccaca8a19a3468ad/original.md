```
Mock([effect])
```

Create a new mocking object that can act as a replacement for a function.

## Effects

Use the `effect` argument to determine what happens upon calling the mock.

  * If the value is callable, then it is called with the same arguments and keywords.
  * If the value is an `Exception`, then the exception is thrown.
  * If the value is a `Vector`, then each call consumes the next element. Nested `Vector`s are returned, but callables and exceptions are treated as explained above.
  * Any other value is returned without modification.

By default, calling a `Mock` returns a new `Mock`.
