```
comp_psd(x::AbstractArray{T}, fs::Real; kwargs...) where {T <: Real}
```

Compute power spectral density using periodogram or welch method.

# Arguments

  * `x`: Time series data (time × channels)
  * `fs`: Sampling frequency
  * `dims=ndims(x)`: Dimension along which to compute PSD
  * `method="periodogram"`: Method to use ("periodogram" or "welch")
  * `window=dsp.hamming`: Window function
  * `n=div(size(x,dims),8)`: Window size for Welch method
  * `noverlap=div(n,2)`: Overlap for Welch method

# Returns

  * `power`: Power spectral density values
  * `freqs`: Corresponding frequencies

# Notes

  * For Welch method, carefully consider window size and overlap
  * Uses DSP.jl for underlying computations
