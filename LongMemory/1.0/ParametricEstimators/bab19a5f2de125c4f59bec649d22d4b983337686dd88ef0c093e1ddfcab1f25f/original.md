```
fi_cor_vals(T::Int,d::Real)
```

Computes the autocorrelation function of the fractional differenced process with parameter `d` at lags 0, 1, ..., `T-1`.

# Arguments

  * `T::Int`: The number of lags to compute.
  * `d::Real`: The fractional differencing parameter.

# Output

  * `vars::Array`: The autocorrelation function of the fractional differenced process with parameter `d` at lags 0, 1, ..., `T-1`.

# Notes

This function uses fi*var*vals() to compute the autocovariance function and then normalizes by the variance (first computed value). 

# Examples

```julia
julia> fi_cor_vals(10, 0.4)
```
