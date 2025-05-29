```
updatable_cholesky(A::AbstractMatrix, m::Int = 2size(A, 1); check::Bool = true)
```

Computes an updatable Cholesky factorization starting with the `n by n` matrix `A`, and pre-allocates an `m x m` matrix for future additions to the matrix (defaults to twice the size `2n`).
