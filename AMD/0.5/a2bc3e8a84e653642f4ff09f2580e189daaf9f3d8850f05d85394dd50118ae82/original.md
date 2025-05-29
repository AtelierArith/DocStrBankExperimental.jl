```
symamd(A)
symamd(A, meta)
```

Given a symmetric or hermitian matrix `A`, symamd computes a permutation vector `p` such that the Cholesky factorization of `A[p,p]` has less fill-in and requires fewer floating point operations than that of A.
