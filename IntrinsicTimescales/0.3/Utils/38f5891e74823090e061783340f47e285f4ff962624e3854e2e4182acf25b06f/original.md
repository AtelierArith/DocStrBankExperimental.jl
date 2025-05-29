```
find_knee_frequency(psd, freqs; dims=ndims(psd), min_freq=freqs[1], max_freq=freqs[end])
```

Find knee frequency by fitting Lorentzian to power spectral density.

# Arguments

  * `psd::AbstractArray{T}`: Power spectral density values
  * `freqs::Vector{T}`: Frequency values
  * `dims::Int=ndims(psd)`: Dimension along which to compute
  * `min_freq::T=freqs[1]`: Minimum frequency to consider
  * `max_freq::T=freqs[end]`: Maximum frequency to consider
  * `constrained::Bool=false`: Whether to use constrained optimization
  * `allow_variable_exponent::Bool=false`: Whether to allow variable exponent (PLE)

# Returns

  * Vector of the fit  for the equation amp/(1 + (f/knee)^{exponent}).

If allow*variable*exponent=false, assumes exponent=2 and returns [amplitude, knee*frequency]. If true,  returns [amplitude, knee*frequency, exponent].

# Notes

  * Uses Lorentzian fitting with NonlinearSolve.jl
  * Initial guess for amplitude is based average value of low frequency power. For knee, this is half-power point. For exponent, it is 2.0.
