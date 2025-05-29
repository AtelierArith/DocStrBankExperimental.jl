```
comp_ac_time(data::AbstractArray{T}, max_lag::Integer; dims::Int=ndims(data)) where {T <: Real}
```

Compute autocorrelation in time domain along specified dimension.

# Arguments

  * `data`: Array of time series data
  * `max_lag`: Maximum lag to compute
  * `dims`: Dimension along which to compute autocorrelation (defaults to last dimension)

# Returns

Array with autocorrelation values, the specified dimension becomes the dimension of lags while the other dimensions denote ACF values
