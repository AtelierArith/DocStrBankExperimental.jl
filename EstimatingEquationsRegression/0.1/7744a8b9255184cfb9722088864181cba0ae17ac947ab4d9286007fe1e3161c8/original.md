```
fit(GeneralizedEstimatingEquationsModel, X, y, g, d, c, [l = canonicallink(d)]; <keyword arguments>)
```

Fit a generalized linear model to data using generalized estimating equations.  `X` and `y` can either be a matrix and a vector, respectively, or a formula and a data frame. `g` is a vector containing group labels, and elements in a group must be consecutive in the data.  `d` must be a `UnivariateDistribution`, `c` must be a `CorStruct` and `l` must be a [`Link`](@ref), if supplied.

# Keyword Arguments

  * `cov_type::String`: Type of covariance estimate for parameters. Defaults

to "robust", other options are "naive", "md" (Mancl-DeRouen debiased) and "kc" (Kauermann-Carroll debiased).xs

  * `dofit::Bool=true`: Determines whether model will be fit
  * `wts::Vector=similar(y,0)`: Not implemented.

Can be length 0 to indicate no weighting (default).

  * `offset::Vector=similar(y,0)`: offset added to `Xβ` to form `eta`.  Can be of

length 0

  * `verbose::Bool=false`: Display convergence information for each iteration
  * `maxiter::Integer=100`: Maximum number of iterations allowed to achieve convergence
  * `atol::Real=1e-6`: Convergence is achieved when the relative change in

`β` is less than `max(rtol*dev, atol)`.

  * `rtol::Real=1e-6`: Convergence is achieved when the relative change in

`β` is less than `max(rtol*dev, atol)`.

  * `start::AbstractVector=nothing`: Starting values for beta. Should have the

same length as the number of columns in the model matrix.

  * `fitcoef::Bool=true`: If false, set the coefficients equal to the GLM coefficients

or to `start` if provided, and update the correlation parameters and dispersion without using GEE iterations to update the coefficients.`

  * `fitcor::Bool=true`: If false, hold the correlation parameters equal to their starting

values.

  * `bccor::Bool=true`: If false, do not compute the Kauermann-Carroll and Mancel-DeRouen

covariances.
