```
fi_var_matrix(T::Int, d::Real)
```

Constructs the autocovariance matrix of the fractional differenced process with parameter `d` at lags 0, 1, ..., `T-1`.

# Arguments

  * `T::Int`: The number of lags to compute.
  * `d::Real`: The fractional differencing parameter.

# Output

  * `V::Array`: The autocovariance matrix of the fractional differenced process with parameter `d` at lags 0, 1, ..., `T-1`.

# Examples

```julia
julia> fi_var_matrix(10, 0.4)
```
