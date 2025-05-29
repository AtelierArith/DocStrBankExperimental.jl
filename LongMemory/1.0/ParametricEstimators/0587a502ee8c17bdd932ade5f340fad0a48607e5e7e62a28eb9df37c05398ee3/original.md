```
csa_var_vals(T::Int, p::Real, q::Real)
```

Computes the autocovariance function of the CSA process with parameters `p` and `q` at lags 0, 1, ..., `T-1`.

# Arguments

  * `T::Int`: The number of lags to compute.
  * `p::Real`: The first parameter of the CSA process.
  * `q::Real`: The second parameter of the CSA process.

# Output

  * `acf::Array`: The autocovariance function of the CSA process with parameters `p` and `q` at lags 0, 1, ..., `T-1`.

# Notes

This function uses the recursive formula for the autocovariance function of the CSA process.

# Examples

```julia
julia> csa_var_vals(20, 0.4, 0.6)
```
