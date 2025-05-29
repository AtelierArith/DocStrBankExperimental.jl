```
NoiseScore
```

Noise estimate error z-score data structure, containing the z-scores for a [`NoiseError`](@ref) with respect to some predicted [`Merit`](@ref).

# Fields

  * `gls_z_score::Float64`: Generalised least squares z-score.
  * `gls_proj_z_score::Float64`: Generalised least squares projected z-score.
  * `gls_marginal_z_score::Float64`: Generalised least squares marginal z-score.
  * `gls_proj_marginal_z_score::Float64`: Generalised least squares projected marginal z-score.
  * `gls_relative_z_score::Float64`: Generalised least squares relative z-score.
  * `gls_proj_relative_z_score::Float64`: Generalised least squares projected relative z-score.
  * `wls_z_score::Float64`: Weighted least squares z-score.
  * `wls_proj_z_score::Float64`: Weighted least squares projected z-score.
  * `wls_marginal_z_score::Float64`: Weighted least squares marginal z-score.
  * `wls_proj_marginal_z_score::Float64`: Weighted least squares projected marginal z-score.
  * `wls_relative_z_score::Float64`: Weighted least squares relative z-score.
  * `wls_proj_relative_z_score::Float64`: Weighted least squares projected relative z-score.
  * `ols_z_score::Float64`: Ordinary least squares z-score.
  * `ols_proj_z_score::Float64`: Ordinary least squares projected z-score.
  * `ols_marginal_z_score::Float64`: Ordinary least squares marginal z-score.
  * `ols_proj_marginal_z_score::Float64`: Ordinary least squares projected marginal z-score.
  * `ols_relative_z_score::Float64`: Ordinary least squares relative z-score.
  * `ols_proj_relative_z_score::Float64`: Ordinary least squares projected relative z-score.
