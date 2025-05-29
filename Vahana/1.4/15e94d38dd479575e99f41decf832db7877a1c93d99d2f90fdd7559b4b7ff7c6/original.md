```
add_agent!(sim, agent::T)::AgentID
```

Add a single agent of type T to the simulation `sim`.

T must have been previously registered by calling [`register_agenttype!`](@ref).

`add_agent!` returns a new AgentID, which can be used to create edges from or to this agent until [`finish_init!`](@ref) is called (in the case that `add_agent!` is called in the initialization phase), or until the transition funcion is finished (in the case that `add_agent!` is called in an [`apply!`](@ref) callback). Do not use the ID for other purposes, they are not guaranteed to be stable.

See also [`add_agents!`](@ref), [`add_edge!`](@ref) and [`add_edges!`](@ref)
