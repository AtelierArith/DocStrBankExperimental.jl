```
run_posterior_predict_checks(samples, paramnames, t, y, yerr, f0, fM, model, with_log_transform; plots="all", n_samples=200, path="", basis_function="SHO", n_frequencies=1000, plot_f_P=false, n_components=20)
```

Run the posterior predictive checks for the model and the approximation of the PSD

# Arguments

  * `samples::Array{Float64, 2}` : The samples from the posterior distribution
  * `paramnames::Array{String, 1}` : The names of the parameters
  * `t::Array{Float64, 1}` : The time series
  * `y::Array{Float64, 1}` : The values of the time series
  * `yerr::Array{Float64, 1}` : The errors of the time series
  * `f0::Float64` : The minimum frequency for the approximation of the PSD
  * `fM::Float64` : The maximum frequency for the approximation of the PSD
  * `model::Function` : The model
  * `with_log_transform::Bool` : If true, the flux is log-transformed
  * `plots::String or Array{String, 1}` : The type of plots to make. It can be "all", "psd", "lsp", "timeseries" or a combination of them in an array
  * `n_samples::Int=200` : The number of samples to draw from the posterior predictive distribution
  * `path::String="all"` : The path to save the plots
  * `basis_function::String="SHO"` : The basis function for the approximation of the PSD
  * `n_frequencies::Int=1000` : The number of frequencies to use for the approximation of the PSD
  * `plot_f_P::Bool=false` : If true, the plots are made in terms of f * PSD
  * `n_components::Int=20` : The number of components to use for the approximation of the PSD
