```
fi_var_vals(T::Int,d::Real)
```

Computes the autocovariance function of the fractional differenced process with parameter `d` at lags 0, 1, ..., `T-1`.

# Arguments

  * `T::Int`: The number of lags to compute.
  * `d::Real`: The fractional differencing parameter.

# Output

  * `vars::Array`: The autocovariance function of the fractional differenced process with parameter `d` at lags 0, 1, ..., `T-1`.

# Notes

This function uses the recursive formula for the autocovariance function of the fractional differenced process. 

# Examples

```julia
julia> fi_var_vals(10, 0.4)
```
