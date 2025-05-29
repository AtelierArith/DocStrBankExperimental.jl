```
struct UnadaptedFunction{F,T} <: Function
```

An instance `FunctionNotAdaptable{F,T}()` signifies that functions of type `F` can't be adapted to inputs of type `T`.

`(f::UnadaptedFunction).f``contains the original function, and`(f::UnadaptedFunction)(args...; kwargs...)` calls the original function.
