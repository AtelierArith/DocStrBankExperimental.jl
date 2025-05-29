```
BrimijoinGaussianSmoothed(; kwargs...) <: BinnedStimgen
```

Stimulus generation type in which      each tonotopic bin is filled by a Gaussian      with a maximum amplitude value chosen     from an equidistant list with equal probability.

# Keywords

  * `min_freq::Real = 100`: The minimum frequency in range from which to sample.
  * `max_freq::Real = 22e3`: The maximum frequency in range from which to sample.
  * `duration::Real = 0.5`: The length of time for which stimuli are played in seconds.
  * `Fs::Real = 44.1e3`: The frequency of the stimuli in Hz.
  * `amp_min::Real = -20`: The lowest dB value a bin can have.
  * `amp_max::Real = 0`: The highest dB value a bin can have.
  * `amp_step::Int = 6`: The number of evenly spaced steps between `amp_min` and `amp_max`.
  * `n_bins::Integer = 100`: The number of bins into which to partition the frequency range.
