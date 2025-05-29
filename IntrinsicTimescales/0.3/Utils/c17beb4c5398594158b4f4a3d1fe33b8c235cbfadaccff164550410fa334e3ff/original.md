```
acw0(lags, acf; dims=ndims(acf))
```

Compute the ACW0 (autocorrelation width at zero crossing) along specified dimension.

# Arguments

  * `lags::AbstractVector{T}`: Vector of lag values
  * `acf::AbstractArray{T}`: Array of autocorrelation values
  * `dims::Int=ndims(acf)`: Dimension along which to compute ACW0

# Returns

  * First lag where autocorrelation crosses zero

# Notes

  * Alternative measure of characteristic timescale
  * More sensitive to noise than ACW50
