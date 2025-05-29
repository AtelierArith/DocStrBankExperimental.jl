```
glm(formula, data,
    distr::UnivariateDistribution, link::Link = canonicallink(distr); <keyword arguments>)
glm(X::AbstractMatrix, y::AbstractVector,
    distr::UnivariateDistribution, link::Link = canonicallink(distr); <keyword arguments>)
```

Fit a generalized linear model to data. Alias for `fit(GeneralizedLinearModel, ...)`.

In the first method, `formula` must be a [StatsModels.jl `Formula` object](https://juliastats.org/StatsModels.jl/stable/formula/) and `data` a table (in the [Tables.jl](https://tables.juliadata.org/stable/) definition, e.g. a data frame). In the second method, `X` must be a matrix holding values of the independent variable(s) in columns (including if appropriate the intercept), and `y` must be a vector holding values of the dependent variable. In both cases, `distr` must specify the distribution, and `link` may specify the link function (if omitted, it is taken to be the canonical link for `distr`; see [`Link`](@ref) for a list of built-in links).

# Keyword Arguments

  * `dropcollinear::Bool=true`: Controls whether or not `lm` accepts a model matrix which is less-than-full rank. If `true` (the default) the coefficient for redundant linearly dependent columns is `0.0` and all associated statistics are set to `NaN`. Typically from a set of linearly-dependent columns the last ones are identified as redundant (however, the exact selection of columns identified as redundant is not guaranteed).
  * `dofit::Bool=true`: Determines whether model will be fit
  * `wts::Vector=similar(y,0)`: Prior frequency (a.k.a. case) weights of observations. Such weights are equivalent to repeating each observation a number of times equal to its weight. Do note that this interpretation gives equal point estimates but different standard errors from analytical (a.k.a. inverse variance) weights and from probability (a.k.a. sampling) weights which are the default in some other software. Can be length 0 to indicate no weighting (default).
  * `offset::Vector=similar(y,0)`: offset added to `Xβ` to form `eta`.  Can be of length 0
  * `verbose::Bool=false`: Display convergence information for each iteration
  * `maxiter::Integer=30`: Maximum number of iterations allowed to achieve convergence
  * `atol::Real=1e-6`: Convergence is achieved when the relative change in deviance is less than `max(rtol*dev, atol)`.
  * `rtol::Real=1e-6`: Convergence is achieved when the relative change in deviance is less than `max(rtol*dev, atol)`.
  * `minstepfac::Real=0.001`: Minimum line step fraction. Must be between 0 and 1.
  * `start::AbstractVector=nothing`: Starting values for beta. Should have the same length as the number of columns in the model matrix.
