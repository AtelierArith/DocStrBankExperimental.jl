```
ReverseCholesky <: Factorization
```

Matrix factorization type of the reverse Cholesky factorization of a dense symmetric/Hermitian positive definite matrix `A`. This is the return type of [`reversecholesky`](@ref), the corresponding matrix factorization function.

The triangular reverse Cholesky factor can be obtained from the factorization `F::ReverseCholesky` via `F.L` and `F.U`, where `A ≈ F.U * F.U' ≈ F.L' * F.L`. ```
