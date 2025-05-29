```
UniformNoiseNoBins(; kwargs...) <: Stimgen
```

Stimulus generation type in which      each frequency is chosen from a uniform distribution on [-100, 0] dB.

# Keywords

  * `min_freq::Real = 100`: The minimum frequency in range from which to sample.
  * `max_freq::Real = 22e3`: The maximum frequency in range from which to sample.
  * `duration::Real = 0.5`: The length of time for which stimuli are played in seconds.
  * `Fs::Real = 44.1e3`: The frequency of the stimuli in Hz.
