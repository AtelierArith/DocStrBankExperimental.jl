```
opCholesky(M, [check=false])
```

Inverse of a Hermitian and positive definite matrix as a linear operator using its Cholesky factorization.  The factorization is computed only once. The optional `check` argument will perform cheap hermicity and definiteness checks. This Operator is not in-place when using `mul!`.
