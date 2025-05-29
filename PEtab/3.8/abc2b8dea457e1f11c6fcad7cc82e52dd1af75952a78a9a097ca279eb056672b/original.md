```
to_chains(res, target::PEtabLogDensity; kwargs...)::MCMCChains
```

Converts Bayesian inference results obtained with `PEtabLogDensity` into an `MCMCChains`.

`res` can be the inference results from AdvancedHMC.jl or AdaptiveMCMC.jl. The returned chain has the parameters on the prior scale.

# Keyword Arguments

  * `start_time`: Optional starting time for the inference, obtained with `now()`.
  * `end_time`: Optional ending time for the inference, obtained with `now()`.

!!! note
    To use this function, the MCMCChains package must be loaded: `using MCMCChains`

