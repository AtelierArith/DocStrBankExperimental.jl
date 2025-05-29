```
acw_romberg(lags, acf)
```

Calculate the area under the curve of ACF using Romberg integration.

# Arguments

  * `dt::Real`: Time step
  * `acf::AbstractVector`: Array of autocorrelation values

# Returns

  * AUC of ACF

# Notes

  * Returns only the integral value, discarding the error estimate
