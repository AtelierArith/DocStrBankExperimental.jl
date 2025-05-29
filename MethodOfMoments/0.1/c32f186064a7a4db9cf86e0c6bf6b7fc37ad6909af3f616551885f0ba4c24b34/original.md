```
BayesianGMM(vce::CovarianceEstimator,
    g, dg, params, nmoment::Integer, nobs::Integer; kwargs...)
```

Construct an object that supports the Bayesian quasi-likelihood evaluations. Arguments provided are defined in the same way as for nonlinear iterated GMM estimation. See documentation website for details.

# Keywords

  * `preg=nothing`: a function for processing the data frame before evaluating moment conditions.
  * `predg=nothing`: a function for processing the data frame before evaluating the derivatives for moment conditions.
  * `deriv=nothing`: specify how gradients for the quasi-posterior functions are computed.
  * `ntasks::Integer=_default_ntasks(nobs*nmoment)`: number of threads use for evaluating moment conditions and their derivatives across observations.
  * `TF::Type=Float64`: type of the numerical values.
