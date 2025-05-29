```
comp_psd_lombscargle(times, data, nanmask, dt; dims=ndims(data))
```

Compute Lomb-Scargle periodogram for data with missing values.

# Arguments

  * `times`: Time points vector
  * `data`: Time series data (may contain NaN)
  * `nanmask`: Boolean mask indicating NaN positions
  * `dt`: Time step
  * `dims=ndims(data)`: Dimension along which to compute

# Returns

  * `power`: Lomb-Scargle periodogram values
  * `frequency_grid`: Corresponding frequencies

# Notes

  * Handles irregular sampling due to missing data
  * Uses frequency grid based on shortest valid time series
  * Automatically determines appropriate frequency range
