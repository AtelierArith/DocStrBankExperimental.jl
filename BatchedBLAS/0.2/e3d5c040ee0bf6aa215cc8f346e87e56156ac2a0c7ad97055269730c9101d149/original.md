```
batched_spmv!(ul, alpha, A, x, beta, y)
```

In-place batched matrix-vector multiplication and addition, equivalent to `y[:,k] = alpha[k] * A[:,:,k] * x[:,k] + beta[k] * y[:,k]` for all `k`. `A` must be packed symmetric, and `uplo` specifies whether the upper ('U') or lower ('L') triangle was packed.  All other inputs can have eltypes of either AbstractFloats or Integers.  `alpha` and `beta` can also be scalars.
