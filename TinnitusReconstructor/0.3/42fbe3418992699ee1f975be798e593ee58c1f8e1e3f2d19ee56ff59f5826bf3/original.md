```
PowerDistribution(; kwargs...) <: BinnedStimgen
```

Stimulus generation type in which      the frequencies in each bin are sampled      from a power distribution learned     from tinnitus examples.

# Keywords

  * `min_freq::Real = 100`: The minimum frequency in range from which to sample.
  * `max_freq::Real = 22e3`: The maximum frequency in range from which to sample.
  * `duration::Real = 0.5`: The length of time for which stimuli are played in seconds.
  * `Fs::Real = 44.1e3`: The frequency of the stimuli in Hz.
  * `n_bins::Integer = 100`: The number of bins into which to partition the frequency range.
  * `distribution_filepath::AbstractString=joinpath(@__DIR__, "distribution.csv")`: The filepath to the default power distribution from which stimuli are generated
