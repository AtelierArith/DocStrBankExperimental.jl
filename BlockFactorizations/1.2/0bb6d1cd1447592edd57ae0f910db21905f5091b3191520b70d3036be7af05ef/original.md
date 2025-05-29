```
BlockFactorization{T} <: Factorization{T}
```

Wrapper type for a matrix of matrices or factorizations `A` with `eltype(A) = T`, which acts as if component matrices were concatenated to form a single matrix `B` with `eltype(B) = T`.
