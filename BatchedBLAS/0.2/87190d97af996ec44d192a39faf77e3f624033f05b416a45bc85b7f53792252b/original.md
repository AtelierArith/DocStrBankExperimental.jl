```
batched_symv!(uplo, alpha, A, x, beta, y)
```

In-place batched matrix-vector multiplication and addition, equivalent to `y[:,k] = alpha[k] * A[:,:,k] * x[:,k] + beta[k] * y[:,k]` for all `k`.  `A` is assumed to be symmetric.  Only the `uplo` (either 'U' or 'L') triangle of `A` is used.  All other inputs can have eltypes of either AbstractFloats or Integers.  `alpha` and `beta` can also be scalars.
