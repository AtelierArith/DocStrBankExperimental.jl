```
comp_ac_fft(data::AbstractArray{T}; dims::Int=ndims(data), n_lags::Integer=size(data, dims)) where {T <: Real}
```

Compute autocorrelation using FFT along specified dimension.

# Arguments

  * `data`: Array of time series data
  * `dims`: Dimension along which to compute autocorrelation (defaults to last dimension)
  * `n_lags`: Number of lags to compute (defaults to size of data along specified dimension)

# Returns

Array with autocorrelation values, the specified dimension becomes the dimension of lags while the other dimensions denote ACF values
