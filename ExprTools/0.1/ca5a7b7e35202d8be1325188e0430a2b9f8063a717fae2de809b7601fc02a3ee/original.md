```
combinedef(def::Dict{Symbol,Any}) -> Expr
```

Create a function definition expression from various components. Typically used to construct a function using the result of [`splitdef`](@ref).

If `def[:head]` is not provided it will default to `:function`.

For more details see the documentation on [`splitdef`](@ref).
