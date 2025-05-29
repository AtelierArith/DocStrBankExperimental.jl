```
ElasticPDMat([m [, chol]]; capacity = 10^3, stepsize = 10^3)
```

Creates an elastic positive definite matrix with initial `capacity = 10^3` and `stepsize = 10^3`. The optional argument `m` is a positive definite, symmetric matrix and `chol` its cholesky decomposition. Use `append!` and `deleteat!` to change an ElasticPDMat.
