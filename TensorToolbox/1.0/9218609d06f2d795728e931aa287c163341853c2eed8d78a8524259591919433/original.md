```
lanczos_tridiag(X,Y,n; <keyword arguments>)
```

Structure exploiting Lanczos tridiagonalization algorithm for n-mode matricization A=(X ∗ Y)ₙ(X ∗ Y)ₙᵀ. Returns orthonormal Q and symmetric tridiagonal T such that A≈Q*T*Q'.

## Arguments:

  * `reqrank::Integer`: Requested rank. Optional.
  * `variant` ∈ {'A','B'} Variant of multiplication (X ∗ Y)ₙ(X ∗ Y)ₙᵀ. Default: 'B'.
  * `tol::Number/Vector`: Tolerance. Default: 1e-8.
  * `maxit`: Maximal number of iterations. Default: 1000.
  * `p::Integer`: Oversampling parameter. Defaul p=10.
