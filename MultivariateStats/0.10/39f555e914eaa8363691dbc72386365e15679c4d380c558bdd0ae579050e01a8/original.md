```
fit(KernelPCA, X; ...)
```

Perform kernel PCA over the data given in a matrix `X`. Each column of `X` is an observation.

This method returns an instance of [`KernelPCA`](@ref).

**Keyword arguments:**

Let `(d, n) = size(X)` be respectively the input dimension and the number of observations:

  * `kernel`: The kernel function. This functions accepts two vector arguments `x` and `y`,

and returns a scalar value (*default:* `(x,y)->x'y`). If set to `nothing`, the matrix `X` is the pre-computed symmetric kernel (Gram) matrix.

  * `solver`: The choice of solver:

      * `:eig`: uses `LinearAlgebra.eigen` (*default*)
      * `:eigs`: uses `Arpack.eigs` (always used for sparse data)
  * `maxoutdim`:  Maximum output dimension (*default* `min(d, n)`)
  * `inverse`: Whether to perform calculation for inverse transform for non-precomputed kernels (*default* `false`)
  * `β`: Hyperparameter of the ridge regression that learns the inverse transform (*default* `1` when `inverse` is `true`).
  * `tol`: Convergence tolerance for `eigs` solver (*default* `0.0`)
  * `maxiter`: Maximum number of iterations for `eigs` solver (*default* `300`)
