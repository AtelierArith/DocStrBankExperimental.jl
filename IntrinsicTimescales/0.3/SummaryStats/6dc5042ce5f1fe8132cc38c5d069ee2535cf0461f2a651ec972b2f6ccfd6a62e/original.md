```
prepare_lombscargle(times, data, nanmask)
```

Prepare data for Lomb-Scargle periodogram computation by handling missing values.

# Arguments

  * `times`: Time points vector
  * `data`: Time series data (may contain NaN)
  * `nanmask`: Boolean mask indicating NaN positions

# Returns

  * `valid_times`: Time points with NaN values removed
  * `valid_data`: Data points with NaN values removed
  * `frequency_grid`: Suggested frequency grid for analysis
