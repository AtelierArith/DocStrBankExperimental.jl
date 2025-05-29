```
lorentzian_initial_guess(psd, freqs; min_freq=freqs[1], max_freq=freqs[end])
```

Estimate initial parameters for Lorentzian fitting.

# Arguments

  * `psd::AbstractVector{<:Real}`: Power spectral density values
  * `freqs::AbstractVector{<:Real}`: Frequency values
  * `min_freq::Real`: Minimum frequency to consider
  * `max_freq::Real`: Maximum frequency to consider

# Returns

  * Vector{Float64}: Initial guess for [amplitude, knee_frequency]

# Notes

  * Estimates amplitude from average power of low frequencies.
  * Estimates knee frequency from half-power point.
  * If allow*variable*exponent=true, sets initial guess for exponent to 2.0.
  * Used as starting point for nonlinear fitting
