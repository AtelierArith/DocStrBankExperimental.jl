```julia
con_3d_agents(
    n::Int64;
    pos,
    space_type,
    agent_type,
    kwargs...
) -> Vector{EasyABM.Agent3D{Float64, EasyABM.PeriodicType, EasyABM.StaticType}}

```

Creates a list of n 3d agents with properties specified as keyword arguments.
