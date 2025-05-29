```
struct FunctionWrapper <: AbstractFunction
    f::Function
    dim::Int
end
```

A function wrapper type that wraps the function `f` where the function `f` is declared to return an output of dimension `dim`.
