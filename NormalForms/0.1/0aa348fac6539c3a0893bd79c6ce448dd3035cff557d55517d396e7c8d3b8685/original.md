```
RowHermite{T<:Integer,M<:AbstractMatrix{T}}
```

Describes the result of a decomposition of an integer matrix `A` into its row-style Hermite normal form `H`, which is upper triangular, and a unimodular matrix `U`, such that `H == U*A`, or equivalently, `A = U\H`.
