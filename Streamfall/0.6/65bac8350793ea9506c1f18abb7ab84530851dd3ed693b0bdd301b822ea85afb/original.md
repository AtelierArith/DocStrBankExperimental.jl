```
run_timestep!(
    node::SimpleHyModNode, climate::Climate, timestep::Int;
    inflow=nothing, extraction=nothing, exchange=nothing
)::Float64
```

Run given HyMod node for a time step.
