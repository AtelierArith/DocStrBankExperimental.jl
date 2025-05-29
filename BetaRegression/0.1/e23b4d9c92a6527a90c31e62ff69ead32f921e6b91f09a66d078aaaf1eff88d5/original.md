```
fit(BetaRegressionModel, formula, data, link=LogitLink(), precisionlink=IdentityLink();
    kwargs...)
```

Fit a [`BetaRegressionModel`](@ref) to the given table `data`, which may be any Tables.jl-compatible table (e.g. a `DataFrame`), using the given `formula`, which can be constructed using `@formula`. In this method, the response and model matrix are determined from the formula and table. It is also possible to provide them explicitly.

```
fit(BetaRegressionModel, X::AbstractMatrix, y::AbstractVector, link=LogitLink(),
    precisionlink=IdentityLink(); kwargs...)
```

Fit a beta regression model using the provided model matrix `X` and response vector `y`. In both of these methods, a link function may be provided, otherwise the default logit link is used. Similarly, a link for the precision may be provided, otherwise the default identity link is used.

## Keyword Arguments

  * `weights`: A vector of weights or `nothing` (default). Currently only `nothing` is accepted.
  * `offset`: An offset vector to be added to the linear predictor or `nothing` (default).
  * `maxiter`: Maximum number of Fisher scoring iterations to use when fitting. Default is 100.
  * `atol`: Absolute tolerance to use when checking for model convergence. Default is `sqrt(eps(T))` where `T` is the type of the estimates.
  * `rtol`: Relative tolerance to use when checking for convergence. Default is the Base default relative tolerance for `T`.

!!! tip
    If you experience convergence issues, you may consider trying a different link for the precision; `LogLink()` is a common choice. Increasing the maximum number of iterations may also be beneficial, especially when working with `Float32`.

