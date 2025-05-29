```
pcaeigen(; kwargs...)
pcaeigen(X; kwargs...)
pcaeigen(X, weights::Weight; kwargs...)
pcaeigen!(X::Matrix, weights::Weight; kwargs...)
```

PCA by Eigen factorization.

  * `X` : X-data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. of principal components (PCs).
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

Let us note D the (n, n) diagonal matrix of weights (`weights.w`) and X the centered matrix in metric D. The function minimizes ||X - T * V'||^2  in metric D, by  computing an Eigen factorization of X' * D * X. 

See function `pcasvd` for examples.
