```
lanczos_tridiag(A; <keyword arguments>)
```

Lanczos tridiagonalization algorithm - returns orthonormal Q and symmetric tridiagonal T such that A≈Q*T*Q'.

## Arguments:

  * `A::Matrix`
  * `tol`: Tolerance. Default: 1e-8.
  * `maxit`: Maximal number of iterations. Default: 1000.
  * `reqrank`: Number of singular values and singular vectors to compute. Optional.
  * `p`: Oversampling parameter. Default: p=10.
