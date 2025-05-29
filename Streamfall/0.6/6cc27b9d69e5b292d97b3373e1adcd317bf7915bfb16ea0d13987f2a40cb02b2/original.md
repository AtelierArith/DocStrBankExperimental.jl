```
run_timestep!(
    node::IHACRESNode, climate::Climate, timestep::Int64;
    inflow=nothing, extraction=nothing, exchange=nothing
)::Float64
```

Run the given IHACRESBilinearNode for a timestep.
