```
lanczos(A; <keyword arguments>)
```

Lanczos based SVD - computes left singular vectors and singular values of a matrix.

## Arguments:

  * `A::Matrix`
  * `tol`: Tolerance - discard singular values below tol. Default: 1e-8.
  * `maxit`: Maximal number of iterations. Default: 1000.
  * `reqrank`: Number of singular values and singular vectors to compute. Optional.
  * `p`: Oversampling parameter. Default: p=10.
