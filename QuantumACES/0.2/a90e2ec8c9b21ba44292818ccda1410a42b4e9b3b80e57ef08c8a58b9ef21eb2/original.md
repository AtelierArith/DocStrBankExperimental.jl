```
NoiseError
```

Noise estimate error data structure containing normalised root-mean-square errors (NRMSE) for a [`NoiseEstimate`](@ref).

# Fields

  * `gls_nrmse::Float64`: Generalised least squares normalised root-mean-square error.
  * `gls_proj_nrmse::Float64`: Generalised least squares projected normalised root-mean-square error.
  * `gls_marginal_nrmse::Float64`: Generalised least squares marginal normalised root-mean-square error.
  * `gls_proj_marginal_nrmse::Float64`: Generalised least squares projected marginal normalised root-mean-square error.
  * `gls_relative_nrmse::Float64`: Generalised least squares relative normalised root-mean-square error.
  * `gls_proj_relative_nrmse::Float64`: Generalised least squares projected relative normalised root-mean-square error.
  * `wls_nrmse::Float64`: Weighted least squares normalised root-mean-square error.
  * `wls_proj_nrmse::Float64`: Weighted least squares projected normalised root-mean-square error.
  * `wls_marginal_nrmse::Float64`: Weighted least squares marginal normalised root-mean-square error.
  * `wls_proj_marginal_nrmse::Float64`: Weighted least squares projected marginal normalised root-mean-square error.
  * `wls_relative_nrmse::Float64`: Weighted least squares relative normalised root-mean-square error.
  * `wls_proj_relative_nrmse::Float64`: Weighted least squares projected relative normalised root-mean-square error.
  * `ols_nrmse::Float64`: Ordinary least squares normalised root-mean-square error.
  * `ols_proj_nrmse::Float64`: Ordinary least squares projected normalised root-mean-square error.
  * `ols_marginal_nrmse::Float64`: Ordinary least squares marginal normalised root-mean-square error.
  * `ols_proj_marginal_nrmse::Float64`: Ordinary least squares projected marginal normalised root-mean-square error.
  * `ols_relative_nrmse::Float64`: Ordinary least squares relative normalised root-mean-square error.
  * `ols_proj_relative_nrmse::Float64`: Ordinary least squares projected relative normalised root-mean-square error.
