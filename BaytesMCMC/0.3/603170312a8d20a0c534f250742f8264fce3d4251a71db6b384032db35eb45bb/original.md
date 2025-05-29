```julia
struct ConfigTuningWindow
```

Default configuration for tuning iterations in each cycle.

# Fields

  * `window::Vector{Int64}`: MCMC Phase tuning window lengths, i.e: 5 = 5 repeats of second window in phasenames
  * `buffer::Vector{Int64}`: (Increasing) Length of windows, i.e.: if window=3, buffer=10 -> total window length: 10-20-30
  * `phasenames::Vector{BaytesMCMC.SamplingPhase}`: Name of phasenames, currently supported: Warmup(), Adaptionˢˡᵒʷ(), Adaptionᶠᵃˢᵗ(), Exploration()
