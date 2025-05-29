```
GaussianNoise(; kwargs...) <: BinnedStimgen
```

Stimulus generation type in which      each tonotopic bin is filled with amplitude chosen from a Gaussian distribution.

# Keywords

  * `min_freq::Real = 100`: The minimum frequency in range from which to sample.
  * `max_freq::Real = 22e3`: The maximum frequency in range from which to sample.
  * `duration::Real = 0.5`: The length of time for which stimuli are played in seconds.
  * `Fs::Real = 44.1e3`: The frequency of the stimuli in Hz.
  * `n_bins::Integer = 100`: The number of bins into which to partition the frequency range.
  * `amplitude_mean::Real = -10`: The mean of the Gaussian.
  * `amplitude_var::Real = 3`: The variance of the Gaussian.
