```
csa_cor_vals(T::Int, p::Real, q::Real)
```

Computes the autocorrelation function of the CSA process with parameters `p` and `q` at lags 0, 1, ..., `T-1`.

# Arguments

  * `T::Int`: The number of lags to compute.
  * `p::Real`: The first parameter of the CSA process.
  * `q::Real`: The second parameter of the CSA process.

# Output

  * `acf::Array`: The autocorrelation function of the CSA process with parameters `p` and `q` at lags 0, 1, ..., `T-1`.

# Notes

This function uses csa*var*vals() to compute the autocovariance function and then normalizes by the variance (first computed value). 

# Examples

```julia
julia> csa_cor_vals(20, 0.4, 0.6)
```
