```
fit(::Type{<:JustIdentifiedLinearGMM}, vce::CovarianceEstimator, data, eqs; kwargs...)
```

Conduct just-identified linear GMM estimation with variance-covariance matrix estimated by `vce`. `data` is a `Tables.jl`-compatible data table. `eqs` specifies the names of the variables. See documentation website for details.

# Keywords

  * `nocons::Bool=false`: do not add constant terms automatically.
  * `initonly::Bool=false`: initialize the returned object without conducting the estimation.
  * `TF::Type=Float64`: type of the numerical values.
