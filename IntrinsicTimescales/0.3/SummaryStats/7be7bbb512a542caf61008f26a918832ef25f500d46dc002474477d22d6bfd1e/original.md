```
comp_ac_time_missing(data::AbstractArray{T}; kwargs...) where {T <: Real}
```

Compute autocorrelation for data with missing values.

# Arguments

  * `data`: Time series data (may contain NaN)
  * `dims=ndims(data)`: Dimension along which to compute
  * `n_lags=size(data,dims)`: Number of lags to compute

# Returns

  * Array of autocorrelation values

# Notes

  * Handles missing data using missing="conservative" approach of

statsmodels.tsa.stattools.acf. See https://www.statsmodels.org/dev/generated/statsmodels.tsa.stattools.acf.html  for details. 
