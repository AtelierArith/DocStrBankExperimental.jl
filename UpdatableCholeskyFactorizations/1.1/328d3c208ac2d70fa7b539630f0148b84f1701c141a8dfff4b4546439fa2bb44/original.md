```
updatable_cholesky!(U_full::AbstractMatrix, n::Int; check::Bool = true)
```

Computes an updatable Cholesky factorization. Assumes that the currently available data `A` is in the upper left `n x n` submatrix.
