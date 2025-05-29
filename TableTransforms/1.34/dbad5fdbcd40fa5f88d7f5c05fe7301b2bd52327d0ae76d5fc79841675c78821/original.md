```
TableTransform
```

A transform that takes a table as input and produces a new table. Any transform implementing the `TableTransform` trait should implement the [`apply`](@ref) function. If the transform [`isrevertible`](@ref), then it should also implement the [`revert`](@ref) function.

A functor interface is automatically generated from the functions above, which means that any transform implementing the `TableTransform` trait can be evaluated directly at any table implementing the [Tables.jl](https://github.com/JuliaData/Tables.jl) interface.
