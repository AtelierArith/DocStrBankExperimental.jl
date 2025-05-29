```
fit(PPCA, X; ...)
```

Perform probabilistic PCA over the data given in a matrix `X`. Each column of `X` is an observation. This method returns an instance of [`PPCA`](@ref).

**Keyword arguments:**

Let `(d, n) = size(X)` be respectively the input dimension and the number of observations:

  * `method`: The choice of methods:

      * `:ml`: use maximum likelihood version of probabilistic PCA (*default*)
      * `:em`: use EM version of probabilistic PCA
      * `:bayes`: use Bayesian PCA
  * `maxoutdim`: Maximum output dimension (*default* `d-1`)
  * `mean`: The mean vector, which can be either of:

      * `0`: the input data has already been centralized
      * `nothing`: this function will compute the mean (*default*)
      * a pre-computed mean vector
  * `tol`: Convergence tolerance (*default* `1.0e-6`)
  * `maxiter`: Maximum number of iterations (*default* `1000`)

**Notes:** This function calls [`ppcaml`](@ref), [`ppcaem`](@ref) or [`bayespca`](@ref) internally, depending on the choice of method.
