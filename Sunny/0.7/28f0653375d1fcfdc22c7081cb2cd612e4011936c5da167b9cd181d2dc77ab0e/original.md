```
add_sample!(sc::SampledCorrelations, sys::System)
add_sample!(sc::SampledCorrelationsStatic, sys::System)
```

Measure pair correlation data for the spin configuration in `sys`, and accumulate these statistics into `sc`. For a dynamical [`SampledCorrelations`](@ref), this involves time-integration of the provided spin trajectory, recording correlations in both space and time. Conversely, [`SampledCorrelationsStatic`](@ref), will record only spatial correlations for the single spin configuration that is provided.

Time-integration will update the spin configuration of `sys` in-place. To avoid this mutation, consider calling [`clone_system`](@ref) prior to `add_sample!`.
