```
lanczos(X,Y,n; <keyword arguments>)
```

Structure exploiting Lanczos based SVD - computes left singular vectors and singular values of n-mode matricization (X ∗ Y)ₙ. Works with matrix (X ∗ Y)ₙ(X ∗ Y)ₙᵀ.

## Arguments:

  * `reqrank::Integer`: Requested rank. Optional.
  * `variant` ∈ {'A','B'} Variant of multiplication (X ∗ Y)ₙ(X ∗ Y)ₙᵀ. Default: 'B'.
  * `tol::Number/Vector`: Tolerance. Default: 1e-8.
  * `maxit`: Maximal number of iterations. Default: 1000.
  * `p::Integer`: Oversampling parameter. Defaul p=10.
