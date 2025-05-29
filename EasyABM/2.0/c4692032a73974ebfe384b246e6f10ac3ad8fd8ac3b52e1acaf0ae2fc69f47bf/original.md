```julia
con_2d_agents(
    n::Int64;
    pos,
    space_type,
    agent_type,
    kwargs...
) -> Vector{EasyABM.Agent2D{Float64, EasyABM.PeriodicType, EasyABM.StaticType}}

```

Creates a list of n 2d agents with properties specified as keyword arguments.
