```
run_timestep!(
    node::GR4JNode, climate::Climate, timestep::Int;
    inflow=nothing, extraction=nothing, exchange=nothing
)
run_timestep!(
    node::GR4JNode, rain::Float64, et::Float64, ts::Int64;
    inflow=nothing, extraction=nothing, exchange=nothing
)
```

Run given GR4J node for a time step.
