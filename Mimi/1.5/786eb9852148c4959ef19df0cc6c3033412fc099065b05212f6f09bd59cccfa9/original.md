```
generate_trials!(sim_inst::SimulationInstance{T}, samples::Int; filename::Union{String, Nothing}=nothing)
```

Generate trials for the given `SimulationInstance` using the defined `samplesize. Call this before running the sim to pre-generate data to be used by all scenarios.  Also saves inputs if a filename is given.
