```
ColumnHermite{T<:Integer,M<:AbstractMatrix{T}}
```

Describes the result of a decomposition of an integer matrix `A` into its row-style Hermite normal form `H`, which is lower triangular, and a unimodular matrix `U`, such that `H == A*U`, or equivalently, `A == H/U`.
