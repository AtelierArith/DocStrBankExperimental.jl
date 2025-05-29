```
batched_gemv!(tA, alpha, A, x, beta, y)
```

In-place batched matrix-vector multiplication and addition, equivalent to `y[:,k] = alpha[k] * A[:,:,k] * x[:,k] + beta[k] * y[:,k]` for all `k`. `A` can optionally be transposed with `tA` as `N`, `T`, or `C`. All other inputs can have eltypes of either AbstractFloats or Integers. `alpha` and `beta` can also be scalars.
