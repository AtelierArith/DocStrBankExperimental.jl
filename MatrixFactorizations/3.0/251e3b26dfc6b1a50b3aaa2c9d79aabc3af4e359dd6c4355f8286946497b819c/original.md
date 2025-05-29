```
reversecholesky(A, NoPivot(); check = true) -> ReverseCholesky
```

Compute the ReverseCholesky factorization of a dense symmetric positive definite matrix `A` and return a [`ReverseCholesky`](@ref) factorization. The matrix `A` can either be a [`Symmetric`](@ref) or [`Hermitian`](@ref) [`AbstractMatrix`](@ref) or a *perfectly* symmetric or Hermitian `AbstractMatrix`.

The triangular ReverseCholesky factor can be obtained from the factorization `F` via `F.L` and `F.U`, where `A ≈ F.U * F.U' ≈ F.L' * F.L`.
