```
UniformPrior(; kwargs...) <: BinnedStimgen
```

Stimulus generation type in which      the number of filled bins is selected from      the Uniform distribution on the interval `[min_bins, max_bins]`.

# Keywords

  * `min_freq::Real = 100`: The minimum frequency in range from which to sample.
  * `max_freq::Real = 22e3`: The maximum frequency in range from which to sample.
  * `duration::Real = 0.5`: The length of time for which stimuli are played in seconds.
  * `Fs::Real = 44.1e3`: The frequency of the stimuli in Hz.
  * `min_bins::Integer = 10`: The minimum number of bins that may be filled on any stimuli.
  * `max_bins::Integer = 50`: The maximum number of bins that may be filled on any stimuli.
  * `n_bins::Integer = 100`: The number of bins into which to partition the frequency range.
