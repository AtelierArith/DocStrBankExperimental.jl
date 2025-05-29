```
colamd(A)
colamd(A, meta)
```

colamd computes a permutation vector `p` such that the Cholesky factorization of   `A[:,p]' * A[:,p]` has less fill-in and requires fewer floating point operations than `AᵀA`.
