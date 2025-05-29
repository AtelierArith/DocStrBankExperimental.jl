```
batched_ger!(alpha, x, y, A)
```

In-place rank-1 update of matrix `A` with vectors `x` and `y` as `alpha[k] * x[:,k] * transpose(y[:,k]) + A[:,:,k]` for all `k`.  All nputs can have eltypes of either AbstractFloats or Integers.  `alpha` can also be a scalar.
