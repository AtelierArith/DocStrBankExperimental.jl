```
AMORS.scale!(x, α::Real) -> x
AMORS.scale!(α::Real, x) -> x
```

Multiply in-place the entries of `x` by the scalar `α` and return `x`. Whatever the values of the entries of `x`, nothing is done if `α = 1` and `x` is zero-filled if `α = 0`.

The AMORS package provides a default implementation of the method that is applicable to any abstract array `x`. The method is expected to be extended for other types of argument `x`.

See also `LinearAlgebra.lmul!(α::Number,x::AbstractArray)` and `LinearAlgebra.rmul!(x::AbstractArray,α::Number)`.
