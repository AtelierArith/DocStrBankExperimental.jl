```
UniformPriorWeightedSampling(; kwargs...) <: BinnedStimgen
```

Stimulus generation type in which      each tonotopic bin is filled from a uniform distribution on [`min_bins`, `max_bins`]     but which bins are filled is determined by a non-uniform distribution.

# Keywords

  * `min_freq::Real = 100`: The minimum frequency in range from which to sample.
  * `max_freq::Real = 22e3`: The maximum frequency in range from which to sample.
  * `duration::Real = 0.5`: The length of time for which stimuli are played in seconds.
  * `Fs::Real = 44.1e3`: The frequency of the stimuli in Hz.
  * `alpha_::Real = 1`: The tuning parameter that exponentiates the number of unique frequencies in each bin.
  * `min_bins::Integer = 10`: The minimum number of bins that may be filled on any stimuli.
  * `max_bins::Integer = 50`: The maximum number of bins that may be filled on any stimuli.
  * `n_bins::Integer = 100`: The number of bins into which to partition the frequency range.
