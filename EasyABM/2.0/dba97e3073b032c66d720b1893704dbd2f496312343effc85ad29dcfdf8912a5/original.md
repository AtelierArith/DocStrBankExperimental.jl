```julia
graph_agents(
    n::Int64;
    node,
    graph_mort_type,
    agent_type,
    kwargs...
) -> Vector{EasyABM.GraphAgent{EasyABM.StaticType, EasyABM.StaticType}}

```

Creates a list of n graph agents with properties specified as keyword arguments.
