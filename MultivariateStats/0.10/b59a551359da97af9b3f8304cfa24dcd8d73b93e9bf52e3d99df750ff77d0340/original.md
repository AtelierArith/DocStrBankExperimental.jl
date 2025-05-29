```
fit(Whitening, X::AbstractMatrix{T}; kwargs...)
```

Estimate a whitening transform from the data given in `X`.

This function returns an instance of [`Whitening`](@ref)

**Keyword Arguments:**

  * `regcoef`: The regularization coefficient. The covariance will be regularized as follows when `regcoef` is positive `C + (eigmax(C) * regcoef) * eye(d)`. Default values is `zero(T)`.
  * `dims`: if `1` the transformation calculated from the row samples. fit standardization parameters in column-wise fashion; if `2` the transformation calculated from the column samples. The default is `nothing`, which is equivalent to `dims=2` with a deprecation warning.
  * `mean`: The mean vector, which can be either of:

      * `0`: the input data has already been centralized
      * `nothing`: this function will compute the mean (**default**)
      * a pre-computed mean vector

**Note:** This function internally relies on [`cov_whitening`](@ref) to derive the transformation `W`.
