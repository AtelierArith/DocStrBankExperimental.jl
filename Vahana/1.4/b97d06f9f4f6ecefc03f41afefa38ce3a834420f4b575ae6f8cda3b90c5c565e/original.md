```
remove_edges!(sim::Simulation, to::AgentID, ::Type{E})
```

Remove all edges of type `E` where `to` is at the target position. 

Can only be called within a transition function, where `E` is in the `write` argument and also in the `add_existing` list of [`apply!`](@ref).
