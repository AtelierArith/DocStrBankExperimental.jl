```
pcaeigenk(; kwargs...)
pcaeigenk(X; kwargs...)
pcaeigenk(X, weights::Weight; kwargs...)
pcaeigenk!(X::Matrix, weights::Weight; kwargs...)
```

PCA by Eigen factorization of the kernel matrix XX'.

  * `X` : X-data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. of principal components (PCs).
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

This is the "kernel cross-product" version of the PCA  algorithm (e.g. Wu et al. 1997). For wide matrices (n << p,  where p is the nb. columns) and n not too large, this algorithm  can be much faster than the others.

Let us note D the (n, n) diagonal matrix of weights (`weights.w`) and X the centered matrix in metric D. The function minimizes ||X - T * V'||^2  in metric D, by  computing an Eigen factorization of D^(1/2) * X * X' D^(1/2).

See function `pcasvd` for examples.

## References

Wu, W., Massart, D.L., de Jong, S., 1997. The kernel PCA  algorithms for wide data. Part I: Theory and algorithms.  Chemometrics and Intelligent Laboratory Systems 36, 165-172. https://doi.org/10.1016/S0169-7439(97)00010-5
