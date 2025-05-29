```
run_diagnostics(prior_samples, variance_samples, f0, fM, model, f_min, f_max; path="", basis_function="SHO", n_components=20)
```

Run the prior predictive checks for the model and the approximation of the PSD

# Arguments

  * `prior_samples::Array{Float64, 2}` : Model samples from the prior distribution
  * `variance_samples::Array{Float64, 1}` : The variance samples
  * `f0::Float64` : The minimum frequency for the approximation of the PSD
  * `fM::Float64` : The maximum frequency for the approximation of the PSD
  * `model::Function` : The model
  * `f_min::Float64` : The minimum frequency of the observed data
  * `f_max::Float64` : The maximum frequency of the observed data
  * `path::String=""` : The path to save the plots
  * `basis_function::String="SHO"` : The basis function for the approximation of the PSD
  * `n_components::Int=20` : The number of components to use for the approximation of the PSD
