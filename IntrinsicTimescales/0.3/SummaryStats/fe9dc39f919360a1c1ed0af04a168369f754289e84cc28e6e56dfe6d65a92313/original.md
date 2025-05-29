```
comp_ac_fft(data::Vector{T}; n_lags::Real=length(data)) where {T <: Real}
```

Compute autocorrelation using FFT method.

# Arguments

  * `data`: Input time series vector
  * `n_lags`: Number of lags to compute (defaults to length of data)

# Returns

  * Vector of autocorrelation values from lag 0 to n_lags-1

# Notes

  * Uses FFT for efficient computation
  * Pads data to next power of 2 for FFT efficiency
  * Normalizes by variance (first lag)
