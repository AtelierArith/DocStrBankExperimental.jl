```
add_agents!(sim, agents)::Vector{AgentID}
```

Add multiple agents at once to the simulation `sim`.

`agents` can be any iterable set of agents, or an arbitrary number of agents as arguments. 

The types of the agents must have been previously registered by calling [`register_agenttype!`](@ref).

`add_agents!` returns a vector of AgentIDs, which can be used to create edges from or to this agents before [`finish_init!`](@ref) is called (in the case that `add_agents!` is called in the initialization phase), or before the transition funcion is finished (in the case that `add_agents!`  is called in an [`apply!`](@ref) callback). Do not use the ID for other purposes, they are not guaranteed to be stable.

See also [`add_agent!`](@ref), [`register_agenttype!`](@ref), [`add_edge!`](@ref) and [`add_edges!`](@ref)
