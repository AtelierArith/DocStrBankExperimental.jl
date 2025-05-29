```
Smith{T,M<:AbstractMatrix{T}} <: Factorization{T}
```

Describes the result of the decomposition of an integer matrix `A` into its Smith normal form `S`, which is diagonal, and unimodular matrices `U` and `V` such that `S == U*A*V`, or equivalently, `A == U\S/V`.
