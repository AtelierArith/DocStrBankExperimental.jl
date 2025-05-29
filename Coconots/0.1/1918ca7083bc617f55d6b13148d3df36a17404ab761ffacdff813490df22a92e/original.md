```
compute_partial_autocorrelation(x, lags)
```

Computes the (partial) autocorrelation of the input vector `x` at the specified `lags`. This function calls `autocor` with demeaning enabled.

# Arguments

  * `x`: A vector of numerical observations.
  * `lags`: A scalar or vector indicating the lag(s) at which to compute the autocorrelation.

# Returns

A vector of autocorrelation coefficients corresponding to the specified lags.
