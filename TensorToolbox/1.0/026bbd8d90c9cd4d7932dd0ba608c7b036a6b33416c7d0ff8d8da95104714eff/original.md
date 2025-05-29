randsvd(A; <keyword arguments>)

Randomized SVD algorithm - returns left singular vectors and singular values of a matrix.

## Arguments:

  * `A::Matrix`
  * `tol`: Tolerance - discard singular values below tol. Default: 1e-8.
  * `maxit`: Maximal number of iterations. Default: 1000.
  * `reqrank`: Number of singular values and singular vectors to compute. Optional.
  * `r`: Number of samples for stopping criterion. Default: r=10.
  * `p`: Oversampling parameter. Default: p=10.
