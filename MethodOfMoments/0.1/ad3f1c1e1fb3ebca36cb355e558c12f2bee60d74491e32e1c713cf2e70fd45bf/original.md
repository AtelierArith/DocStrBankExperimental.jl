```
fit(::Type{<:IteratedLinearGMM}, vce::CovarianceEstimator, data, eqs; kwargs...)
```

Conduct linear iterated GMM estimation with weight matrix in each iteration evaluated as the inverse of variance-covariance matrix estimated by `vce`. `data` is a `Tables.jl`-compatible data table. `eqs` specifies the names of the variables. This method is for the case where the parameters are over-identified. See documentation website for details.

# Keywords

  * `nocons::Bool=false`: do not add constant terms automatically.
  * `winitial=:TSLS`: initial weight matrix; use the one for two-stage least squares by default.
  * `θtol::Real=1e-8`: tolerance level for determining the convergence of parameters.
  * `maxiter::Integer=10000`: maximum number of iterations allowed.
  * `showtrace::Bool=false`: print information as iteration proceeds.
  * `initonly::Bool=false`: initialize the returned object without conducting the estimation.
  * `TF::Type=Float64`: type of the numerical values.
