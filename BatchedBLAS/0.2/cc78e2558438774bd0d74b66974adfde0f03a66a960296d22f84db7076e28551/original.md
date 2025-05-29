```
batched_syr!(uplo, alpha, x, A)
```

In-place rank-1 update of symmetric matrix `A` with vector `x` as `alpha[k] * x[:,k] * transpose(x[:,k]) + A[:,:,k]` for all `k`.  `A` is assumed to be symmetric.  Only the `uplo` (either 'U' or 'L') triangle of `A` is used.  All other inputs can have eltypes of either AbstractFloats or Integers.  `alpha` can also be a scalar.
