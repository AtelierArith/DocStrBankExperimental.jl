```
fit(::Type{<:IteratedGMM}, solvertype, vce::CovarianceEstimator,
    g, dg, params, nmoment::Integer, nobs::Integer; kwargs...)
```

Conduct nonlinear iterated GMM estimation with a solver of `solvertype` and weight matrix in each iteration evaluated as the inverse of variance-covariance matrix estimated by `vce`. Moment conditions and their derivatives are specified as `g` and `dg`. Names of the parameters, number of moment conditions and number of observations are provided as `params`, `nmoment` and `nobs`. See documentation website for details.

# Keywords

  * `preg=nothing`: a function for processing the data frame before evaluating moment conditions.
  * `predg=nothing`: a function for processing the data frame before evaluating the derivatives for moment conditions.
  * `winitial=I`: initial weight matrix; use identify matrix by default.
  * `θtol::Real=1e-8`: tolerance level for determining the convergence of parameters.
  * `maxiter::Integer=10000`: maximum number of iterations allowed.
  * `ntasks::Integer=_default_ntasks(nobs*nmoment)`: number of threads use for evaluating moment conditions and their derivatives across observations.
  * `showtrace::Bool=false`: print information as iteration proceeds.
  * `initonly::Bool=false`: initialize the returned object without conducting the estimation.
  * `solverkwargs=NamedTuple()`: keyword arguments passed to the optimization solver as a `NamedTuple`.
  * `TF::Type=Float64`: type of the numerical values.
