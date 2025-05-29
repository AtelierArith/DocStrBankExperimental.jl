```
sample_approx_model(samples, variance_samples, f0, fM, model; n_frequencies=1_000, basis_function="SHO", n_components=20)
```

Check the approximation of the PSD by computing the residuals and the ratios of the PSD and the approximated PSD

# Arguments

  * `samples::Array{Float64, n}` : The model samples
  * `variance_samples::Array{Float64, 1}` : The variance samples
  * `f0::Float64` : The minimum frequency for the approximation of the PSD
  * `fM::Float64` : The maximum frequency for the approximation of the PSD
  * `model::Function` : The model
  * `n_frequencies::Int=1_000` : The number of frequencies to use for the approximation of the PSD
  * `basis_function::String="SHO"` : The basis function for the approximation of the PSD
  * `n_components::Int=20` : The number of components to use for the approximation of the PSD

# Return

  * `psd::Array{Float64, 2}` : The PSD
  * `psd_approx::Array{Float64, 2}` : The approximated PSD
  * `residuals::Array{Float64, 2}` : The residuals (psd-approx_psd)
  * `ratios::Array{Float64, 2}` : The ratios (approx_psd/psd)
