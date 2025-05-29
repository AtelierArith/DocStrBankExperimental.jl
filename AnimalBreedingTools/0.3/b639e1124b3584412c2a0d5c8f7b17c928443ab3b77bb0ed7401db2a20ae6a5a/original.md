```
bentV = bending2(V [, W], corr=false, mineig=eps, tol=eps, maxiter=10000, force=false, verbose=false)
```

Apply an alternative "bending" method to a variance-covariance matrix `V` using a weighting matrix `W`, as described by Jorjani et al. (2003). When omitting `W`, `J` (matrix of ones) will be used, implying the same weights for all elements. Jorjani et al. (2003) suggested `W` as the reciprocal of number of individuals used in the estimation of covariances.

The function calculates the eigenvalues of `V`, and an eigenvalue is replaced with `mineig` if it is smaller than `mineig`. The covariance matrix is reconstructed with modified eigenvalues, then tests whether it is positive definite by checking the minimum eigenvalue larger than `tol`. The function repeats the process until the resulting matrix becomes positive definite, and the number of maximum iterations is defind by `maxiter`.

See some options below.

  * With `corr=true`, this function assumes the input is a correlation matrix; otherwise, the input is expected to be a variance-covariance matrix.
  * With `force=true`, this function iterates the formula `maxiter` times regardless of whether it has converged or not.
  * With `verbose=true`, this function shows the number of iterations required when `force=false`.
