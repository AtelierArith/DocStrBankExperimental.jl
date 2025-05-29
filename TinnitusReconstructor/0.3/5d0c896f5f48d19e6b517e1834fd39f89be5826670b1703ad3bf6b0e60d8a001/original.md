```
GaussianPrior(; kwargs...) <: BinnedStimgen
```

Stimulus generation type in which      the number of filled bins is selected from      from a Gaussian distribution with known mean and variance parameters.

# Keywords

  * `min_freq::Real = 100`: The minimum frequency in range from which to sample.
  * `max_freq::Real = 22e3`: The maximum frequency in range from which to sample.
  * `duration::Real = 0.5`: The length of time for which stimuli are played in seconds.
  * `Fs::Real = 44.1e3`: The frequency of the stimuli in Hz.
  * `n_bins_filled_var::Real = 1`: The variance of number of bins that may be filled on any stimuli.
  * `n_bins_filled_mean::Integer = 20`: The mean number of bins that may be filled on any stimuli.
  * `n_bins::Integer = 100`: The number of bins into which to partition the frequency range.
