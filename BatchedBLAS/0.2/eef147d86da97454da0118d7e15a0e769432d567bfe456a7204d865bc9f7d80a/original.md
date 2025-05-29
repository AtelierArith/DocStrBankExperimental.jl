```
batched_spr!(uplo, alpha, x, A)
```

In-place rank-1 update of packed symmetric matrix `A` with vector `x` as `alpha[k] * x[:,k] * transpose(x[:,k]) + A[:,:,k]` for all `k`.  `A` must be symmetric, and `uplo` specifies whether the upper ('U') or lower ('L') triangle was packed.  All other inputs can have eltypes of either AbstractFloats or Integers.  `alpha` can also be a scalar.
