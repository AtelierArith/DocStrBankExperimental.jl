```
RobustVCE(nparam::Integer, nmoment::Integer, nobs::Integer; kwargs...)
```

Constuct an object for specifications and cache for heteroskedasticity-robust variance-covariance estimator. The associated GMM problem involves `nparam` parameters, `nmoment` moment conditions and `nobs` sample observations.

# Keywords

  * `adjustdofr::Integer=0`: finite-sample adjustment for the residual degree of freedom.
  * `TF::Type=Float64`: type of the numerical values.
