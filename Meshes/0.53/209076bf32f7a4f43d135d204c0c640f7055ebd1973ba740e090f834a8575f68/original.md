```
atol(T)
atol(x::T)
```

Absolute tolerance used in algorithms for approximate comparison with numbers of type `T`. It is used in the source code in calls to the [`isapprox`](@ref) function:

```julia
isapprox(a::T, b::T, atol=atol(T))
```
