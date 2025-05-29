```
all_agents(sim, ::Type{T}, [all_ranks=true])
```

This function retrieves a vector of the states for all agents of type T of the simulation `sim`.

The `all_ranks` argument determines whether to include agents from all ranks or just the current rank in parallel simulations. When `all_ranks` is `true`, the function returns a vector of all agent identifiers across all ranks.  

The states and IDs of the agents returned by `all_agents` and [`all_agentids`](@ref) are in the same order.

!!! info
    `all_agents` cannot be called within a transition function if the  argument `all_ranks` is set to true.


See also [`all_agentids`](@ref), [`add_agents!`](@ref) and [`num_agents`](@ref).
