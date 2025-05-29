```
cross_periodogram(t, y₁, y₂, y₁_err = nothing, y₂_err = nothing; compute_coherence = true, apply_end_matching = false, subtract_mean = true)
```

Compute the cross-periodogram between two time series y₁ and y₂ with time stamps t using the fast Fourier transform (FFT).

# Arguments

  * `t::Array{Float64, 1}`: Time stamps.
  * `y₁::Array{Float64, 1}`: First time series data. Or a matrix of multiple time series.
  * `y₂::Array{Float64, 1}`: Second time series data. Or a matrix of multiple time series.
  * `y₁_err::Array{Float64, 1}`: Error in the first time series. Or a matrix of errors for multiple time series.
  * `y₂_err::Array{Float64, 1}`: Error in the second time series Or a matrix of errors for multiple time series.
  * `compute_coherence::Bool`: Compute the coherence between the two time series. Default is true.
  * `apply_end_matching::Bool`: Apply end-matching to the data. Default is false.
  * `subtract_mean::Bool`: Subtract the mean from the data. Default is true.

If compute_coherence  is true, the function returns the coherence between the two time series. Otherwise, it returns the cross-periodogram and the mean power spectra of the two time series. see `coherence` function for the optional returns.

# Returns

  * `f::Array{Float64, 1}`: Frequency array.
  * `C̄::Array{Complex{Float64}, 1}`: Mean cross-periodogram.
  * `P̄₁::Array{Float64, 1}`: Mean power spectrum of the first time series.
  * `P̄₂::Array{Float64, 1}`: Mean power spectrum of the second time series.
  * `C::Array{Complex{Float64}, 1}`: Cross-periodogram.
