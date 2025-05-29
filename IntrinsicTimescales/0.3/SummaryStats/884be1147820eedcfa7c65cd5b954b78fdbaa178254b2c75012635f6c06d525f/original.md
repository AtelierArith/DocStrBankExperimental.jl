```
_comp_psd_lombscargle(times, data, frequency_grid)
```

Internal function to compute Lomb-Scargle periodogram for a single time series.

# Arguments

  * `times`: Time points vector (without NaN)
  * `data`: Time series data (without NaN)
  * `frequency_grid`: Pre-computed frequency grid

# Returns

  * `power`: Lomb-Scargle periodogram values
  * `frequency_grid`: Input frequency grid

# Notes

  * Uses LombScargle.jl for core computation
  * Assumes data has been pre-processed and doesn't contain NaN values
  * Normalizes power spectrum by variance
