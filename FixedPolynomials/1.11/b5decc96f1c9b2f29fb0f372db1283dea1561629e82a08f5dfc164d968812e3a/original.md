```
JacobianConfig(F::Vector{Polynomial{T}}, [x::AbstractVector{S}])
```

A data structure with which the jacobian of a `Vector` `F` of `Polynomial`s can be evaluated efficiently. Note that `x` is only used to determine the output type of `F(x)`.

```
JacobianConfig(F::Vector{Polynomial{T}}, [S])
```

Instead of a vector `x` a type can also be given directly.
