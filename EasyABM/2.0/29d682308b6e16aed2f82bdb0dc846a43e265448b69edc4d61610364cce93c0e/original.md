```julia
neighbors_moore(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType}
) -> Base.Generator
neighbors_moore(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType},
    dist::Int64
) -> Base.Generator

```
