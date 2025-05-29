```julia
neighbors(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.StaticType}
) -> Base.Iterators.Filter
neighbors(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.StaticType},
    dist::Real
) -> Base.Iterators.Filter

```

Returns active neighboring agents to given agent within euclidean distance `dist`. 
