```
fit(SpatialPCA, X, W; ...)
```

Perform SpatialPCA over the data given a matrix `X` and `W`. Each column of `X` is an **observation**.  `W` is a connectivity matrix where $w_{ij}$ is the connection from j -> i.

**Keyword arguments**

  * `maxoutdim`: The output dimension, i.e. dimension of the transformed space (*min(d, nc-1)*)
  * `solver`: The choice of solver:

      * `:eig`: uses `LinearAlgebra.eigen` (*default*)
      * `:eigs`: uses `Arpack.eigs` (always used for sparse data)
  * `tol`: Convergence tolerance for `eigs` solver (*default* `0.0`)
  * `maxiter`: Maximum number of iterations for `eigs` solver (*default* `300`)
  * `center_sparse`: Center sparse matrix `X` (dense X will always be centered) (*default* `false`)

**References**

[T. Jombart, et al. "Revealing cryptic spatial patterns in genetic variability by a new multivariate method." *Heredity* (2008)](https://doi.org/10.1038/hdy.2008.34)
