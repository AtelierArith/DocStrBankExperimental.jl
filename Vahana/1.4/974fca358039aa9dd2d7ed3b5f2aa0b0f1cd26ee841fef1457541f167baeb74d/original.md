```
register_agenttype!(types::ModelTypes, ::Type{T}, [hints...])
```

Register an additional agent type to `types`. 

An agent type is a struct that define the state space for agents of type `T`. These structs must be "bits types", meaning the type is immutable and contains only primitive types and other bits types.

By default, it is assumed that an agent can die (be removed from the simulation) by returning `nothing` in the transition function (see [`apply!`](@ref). In the case that agents are never removed, the hint :Immortal can be given to improve the performance of the simulation.

If agents of this type never access the state of other agents of the same type in a transition function (e.g., via agentstate or neighborstates calls), then the :Independent hint can be given. This avoids unnecessary copies of the agents.

A pipeable version of `register_agenttype!` is also available, enabling the construction of a Model via a sequence of `register_*` calls. This pipeline starts with `ModelTypes()` as the source and terminates in the [`create_model`](@ref) function as the destination.

See also [`add_agent!`](@ref) and [`add_agents!`](@ref) 
