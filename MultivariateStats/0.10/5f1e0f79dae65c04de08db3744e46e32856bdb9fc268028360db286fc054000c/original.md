```
fit(FactorAnalysis, X; ...)
```

Perform factor analysis over the data given in a matrix `X`. Each column of `X` is an observation. This method returns an instance of [`FactorAnalysis`](@ref).

**Keyword arguments:**

Let `(d, n) = size(X)` be respectively the input dimension and the number of observations:

  * `method`: The choice of methods:

      * `:em`: use EM version of factor analysis
      * `:cm`: use CM version of factor analysis (*default*)
  * `maxoutdim`: Maximum output dimension (*default* `d-1`)
  * `mean`: The mean vector, which can be either of:

      * `0`: the input data has already been centralized
      * `nothing`: this function will compute the mean (*default*)
      * a pre-computed mean vector
  * `tol`: Convergence tolerance (*default* `1.0e-6`)
  * `maxiter`: Maximum number of iterations (*default* `1000`)
  * `η`: Variance low bound (*default* `1.0e-6`)

**Notes:** This function calls [`facm`](@ref) or [`faem`](@ref) internally, depending on the choice of method.
