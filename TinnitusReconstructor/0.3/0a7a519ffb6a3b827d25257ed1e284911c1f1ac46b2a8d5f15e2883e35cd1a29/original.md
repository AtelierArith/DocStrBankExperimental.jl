```
Bernoulli(; kwargs...) <: BinnedStimgen
```

Stimulus generation type in which      each tonotopic bin has a probability `bin_prob`     of being at 0 dB, otherwise it is at -100 dB.

# Keywords

  * `min_freq::Real = 100`: The minimum frequency in range from which to sample.
  * `max_freq::Real = 22e3`: The maximum frequency in range from which to sample.
  * `duration::Real = 0.5`: The length of time for which stimuli are played in seconds.
  * `Fs::Real = 44.1e3`: The frequency of the stimuli in Hz.
  * `bin_prob::Real=0.3`: The probability of a bin being filled.
  * `n_bins::Integer = 100`: The number of bins into which to partition the frequency range.
