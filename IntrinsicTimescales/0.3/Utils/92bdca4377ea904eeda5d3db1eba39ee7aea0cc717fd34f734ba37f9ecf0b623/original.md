```
find_oscillation_peak(psd, freqs; min_freq=5.0/1000.0, max_freq=50.0/1000.0, min_prominence_ratio=0.1)
```

Find dominant oscillatory peak in power spectral density.

# Arguments

  * `psd::AbstractVector`: Power spectral density values
  * `freqs::AbstractVector`: Frequency values
  * `min_freq::Real=5.0/1000.0`: Minimum frequency to consider
  * `max_freq::Real=50.0/1000.0`: Maximum frequency to consider
  * `min_prominence_ratio::Real=0.1`: Minimum peak prominence as fraction of max PSD

# Returns

  * Frequency of most prominent peak, or NaN if no significant peak found

# Notes

  * Uses peak prominence for robustness
  * Filters peaks by minimum prominence threshold
  * Returns NaN if no peaks meet criteria
