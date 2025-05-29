```
remove_edges!(sim::Simulation, from::AgentID, to::AgentID, ::Type{E})
```

Removes all edges of type `E` with `from` at the source position and `to` at the target position of an edge. `remove_edges!` in this form (with `from` as argument) can only be called if the edge type `E` does not have the `:IgnoreFrom` hint.

Can also only be called within a transition function, where `E` is in the `write` argument and also in the `add_existing` list of [`apply!`](@ref).
