```
@constinferred [AllowedType] f(x)
```

Tests that the call expression `f(x)` returns a value of the same type inferred by the compiler. It is useful to check for type stability. Similar to `Test.@inferred`, but differs in two important ways.

Firstly, `@constinferred` tries to test type stability under constant propagation by testing type stability of a new function, where all arguments or keyword arguments of the original function `f` that have a constant value (in the call expression) of type `Union{Number,Char,Symbol}` are hard coded.

If you want to test for constant propagation in a variable which is not hard-coded in the call expression, you can interpolate it into the expression.

Secondly, @constinferred returns the value if type inference succeeds, like `@inferred`, but used the `Test.@test` mechanism and shows up as an actual test error when type inference fails. ```
