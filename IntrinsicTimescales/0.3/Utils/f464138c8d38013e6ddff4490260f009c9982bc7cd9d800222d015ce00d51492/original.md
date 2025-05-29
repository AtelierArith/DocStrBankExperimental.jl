```
acw50(lags, acf; dims=ndims(acf))
```

Compute the ACW50 (autocorrelation width at 50%) along specified dimension.

# Arguments

  * `lags::AbstractVector{T}`: Vector of lag values
  * `acf::AbstractArray{T}`: Array of autocorrelation values
  * `dims::Int=ndims(acf)`: Dimension along which to compute ACW50

# Returns

  * First lag where autocorrelation falls below 0.5

# Notes

  * Used for estimating characteristic timescales
  * Related to tau by: tau = -acw50/log(0.5)
