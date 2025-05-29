```
abstract type Interpreter end
```

An interpreter that subtypes this type can implement its own evaluation strategies, by overloading the certain methods in JuliaInterpreter that are defined for this base type. The default behavior of `Interpreter` is same as that of [`RecursiveInterpreter`](@ref), meaning it will recursively interpret all `:call` expressions.
