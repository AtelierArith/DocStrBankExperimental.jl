```
NoiseEstimate
```

Noise estimate data structure.

# Fields

  * `eigenvalues_experiment_ensemble::Vector{Vector{Vector{Float64}}}`: Circuit eigenvalue estimates for each tuple and circuit eigenvalue.
  * `covariance_experiment_ensemble::Vector{Vector{Vector{Float64}}}`: Covariance circuit eigenvalue estimates for each tuple and covariance circuit eigenvalue.
  * `shot_budget::Int`: Shot budget for the (potentially randomised) experimental ensemble.
  * `gls_unproj_gate_eigenvalues::Vector{Float64}`: Generalised least squares unprojected gate eigenvalues.
  * `gls_gate_eigenvalues::Vector{Float64}`: Generalised least squares projected gate eigenvalues.
  * `gls_unproj_gate_probabilities::Dict{Gate, Vector{Float64}}`: Generalised least squares unprojected gate error probabilities.
  * `gls_gate_probabilities::Dict{Gate, Vector{Float64}}`: Generalised least squares projected gate error probabilities.
  * `gls_unproj_marginal_gate_eigenvalues::Vector{Float64}`: Generalised least squares unprojected marginal gate eigenvalues.
  * `gls_marginal_gate_eigenvalues::Vector{Float64}`: Generalised least squares projected marginal gate eigenvalues.
  * `gls_unproj_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: Generalised least squares unprojected marginal gate error probabilities.
  * `gls_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: Generalised least squares projected marginal gate error probabilities.
  * `gls_unproj_relative_gate_eigenvalues::Vector{Float64}`: Generalised least squares unprojected relative gate eigenvalues.
  * `gls_relative_gate_eigenvalues::Vector{Float64}`: Generalised least squares projected relative gate eigenvalues.
  * `wls_unproj_gate_eigenvalues::Vector{Float64}`: Weighted least squares unprojected gate eigenvalues.
  * `wls_gate_eigenvalues::Vector{Float64}`: Weighted least squares projected gate eigenvalues.
  * `wls_unproj_gate_probabilities::Dict{Gate, Vector{Float64}}`: Weighted least squares unprojected gate error probabilities.
  * `wls_gate_probabilities::Dict{Gate, Vector{Float64}}`: Weighted least squares projected gate error probabilities.
  * `wls_unproj_marginal_gate_eigenvalues::Vector{Float64}`: Weighted least squares unprojected marginal gate eigenvalues.
  * `wls_marginal_gate_eigenvalues::Vector{Float64}`: Weighted least squares projected marginal gate eigenvalues.
  * `wls_unproj_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: Weighted least squares unprojected marginal gate error probabilities.
  * `wls_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: Weighted least squares projected marginal gate error probabilities.
  * `wls_unproj_relative_gate_eigenvalues::Vector{Float64}`: Weighted least squares unprojected relative gate eigenvalues.
  * `wls_relative_gate_eigenvalues::Vector{Float64}`: Weighted least squares projected relative gate eigenvalues.
  * `ols_unproj_gate_eigenvalues::Vector{Float64}`: Ordinary least squares unprojected gate eigenvalues.
  * `ols_gate_eigenvalues::Vector{Float64}`: Ordinary least squares projected gate eigenvalues.
  * `ols_unproj_gate_probabilities::Dict{Gate, Vector{Float64}}`: Ordinary least squares unprojected gate error probabilities.
  * `ols_gate_probabilities::Dict{Gate, Vector{Float64}}`: Ordinary least squares projected gate error probabilities.
  * `ols_unproj_marginal_gate_eigenvalues::Vector{Float64}`: Ordinary least squares unprojected marginal gate eigenvalues.
  * `ols_marginal_gate_eigenvalues::Vector{Float64}`: Ordinary least squares projected marginal gate eigenvalues.
  * `ols_unproj_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: Ordinary least squares unprojected marginal gate error probabilities.
  * `ols_marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: Ordinary least squares projected marginal gate error probabilities.
  * `ols_unproj_relative_gate_eigenvalues::Vector{Float64}`: Ordinary least squares unprojected relative gate eigenvalues.
  * `ols_relative_gate_eigenvalues::Vector{Float64}`: Ordinary least squares projected relative gate eigenvalues.
