```
matrixrepr!(f, a::AbstractMatrix, b1::AbstractBasis, b0::AbstractBasis; iszero::Bool = false) -> a
```

Compute a matrix representing the linear map `f` with with respect to the bases `b0` (source) and `b1` (target). Store the result in `a` and return `a`. If the keyword argument `iszero` is `true`, then the matrix `a` is not first initialized with zeros.

See also [`matrixrepr`](@ref).
