```
comp_psd_adfriendly(x::AbstractArray{<:Real}, fs::Real; dims::Int=ndims(x))
```

Compute power spectral density using an automatic differentiation (AD) friendly implementation.

# Arguments

  * `x`: Time series data
  * `fs`: Sampling frequency
  * `dims=ndims(x)`: Dimension along which to compute PSD

# Returns

  * `power`: Power spectral density values
  * `freqs`: Corresponding frequencies
