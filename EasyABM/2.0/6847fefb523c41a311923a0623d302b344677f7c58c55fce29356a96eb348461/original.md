```julia
neighbors(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.StaticType}
) -> Base.Iterators.Filter
neighbors(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.StaticType},
    dist::Real
) -> Base.Iterators.Filter

```

Returns active neighboring agents to given agent within euclidean distance `dist`. 
