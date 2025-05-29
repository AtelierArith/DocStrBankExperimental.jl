```julia
neighbors_moore(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType}
) -> Base.Generator
neighbors_moore(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType},
    dist::Int64
) -> Base.Generator

```
