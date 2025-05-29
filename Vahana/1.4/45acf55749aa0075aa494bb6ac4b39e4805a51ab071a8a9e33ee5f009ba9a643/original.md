```
all_agentids(sim, ::Type{T}, [all_ranks=true])
```

This function retrieves a vector of the current ids for all agents of type T of the simulation `sim`. 

These ids are not stable and can change during parallel simulations, e.g. by calling [`finish_init!`](@ref) (and hopefully in the future through dynamic load balancing).

The `all_ranks` argument determines whether to include agents from all ranks or just the current rank in parallel simulations. When `all_ranks` is `true`, the function returns a vector of all agent identifiers across all ranks.  

The states and IDs of the agents returned by [`all_agents`](@ref) and `all_agentids` are in the same order.

!!! info
    `all_agentids` cannot be called within a transition function if the  argument `all_ranks` is set to true.


See also [`all_agents`](@ref), [`add_agents!`](@ref) and [`num_agents`](@ref).
