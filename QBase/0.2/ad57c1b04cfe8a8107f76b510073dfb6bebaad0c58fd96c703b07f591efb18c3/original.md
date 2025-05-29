```
is_hermitian( M :: AbstractMatrix{<:Number}; atol=ATOL :: Float64 ) :: Bool
```

Returns `true` if the supplied matrix is hermitian (self-adjoint), `M == M'`.
