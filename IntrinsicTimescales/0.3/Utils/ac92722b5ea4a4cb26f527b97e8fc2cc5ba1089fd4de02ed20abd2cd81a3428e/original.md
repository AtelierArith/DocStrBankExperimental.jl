```
expdecay(tau, lags)
```

Compute exponential decay function.

# Arguments

  * `tau::Real`: Timescale parameter
  * `lags::AbstractVector`: Time lags

# Returns

  * Vector of exp(-t/tau) values

# Notes

  * Used for fitting autocorrelation functions
  * Assumes exponential decay model: acf = exp(-t/tau)
