```
fooof_fit(psd, freqs; dims=ndims(psd), min_freq=freqs[1], max_freq=freqs[end], 
          oscillation_peak=true, max_peaks=3)
```

Perform FOOOF-style fitting of power spectral density. The default behavior is to fit a Lorentzian with PLE = 2.  If allow*variable*exponent=true, the function will fit a Lorentzian with variable PLE. 

# Arguments

  * `psd::AbstractArray{T}`: Power spectral density values
  * `freqs::Vector{T}`: Frequency values
  * `dims::Int=ndims(psd)`: Dimension along which to compute
  * `min_freq::T=freqs[1]`: Minimum frequency to consider
  * `max_freq::T=freqs[end]`: Maximum frequency to consider
  * `oscillation_peak::Bool=true`: Whether to compute oscillation peaks
  * `max_peaks::Int=3`: Maximum number of oscillatory peaks to fit
  * `allow_variable_exponent::Bool=false`: Whether to allow variable exponent (PLE)
  * `constrained::Bool=false`: Whether to use constrained optimization

# Returns

If return*only*knee=false:

  * Tuple of (knee*frequency, oscillation*parameters) where oscillation*parameters is Vector of (center*freq, amplitude, std_dev) for each peak

If return*only*knee=true:

  * knee_frequency only

# Notes

  * Implements iterative FOOOF-style fitting:

    1. Fit initial Lorentzian to PSD
    2. Find and fit Gaussian peaks iteratively
    3. Subtract all Gaussians from original PSD
    4. Refit Lorentzian to cleaned PSD
