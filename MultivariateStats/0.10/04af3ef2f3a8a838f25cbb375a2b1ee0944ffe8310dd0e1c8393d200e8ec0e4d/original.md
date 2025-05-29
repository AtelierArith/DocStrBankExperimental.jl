```
fit(CCA, X, Y; ...)
```

Perform CCA over the data given in matrices `X` and `Y`. Each column of `X` and `Y` is an observation.

`X` and `Y` should have the same number of columns (denoted by `n` below).

This method returns an instance of [`CCA`](@ref).

**Keyword arguments:**

  * `method`: The choice of methods:

      * `:cov`: based on covariance matrices
      * `:svd`: based on SVD of the input data (*default*)
  * `outdim`: The output dimension, *i.e* dimension of the common space (*default*: `min(dx, dy, n)`)
  * `mean`: The mean vector, which can be either of:

      * `0`: the input data has already been centralized
      * `nothing`: this function will compute the mean (*default*)
      * a pre-computed mean vector

**Notes:** This function calls [`ccacov`](@ref) or [`ccasvd`](@ref) internally, depending on the choice of method.
