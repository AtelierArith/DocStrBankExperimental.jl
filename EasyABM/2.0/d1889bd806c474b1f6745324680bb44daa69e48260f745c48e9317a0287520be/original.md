```julia
neighbors(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType}
) -> Union{Base.Generator{I, typeof(identity)} where I<:(Array{EasyABM.Agent3D{S, P, EasyABM.MortalType}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType}), Base.Iterators.Filter}
neighbors(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType},
    dist::Real
) -> Union{Base.Generator{I, typeof(identity)} where I<:(Array{EasyABM.Agent3D{S, P, EasyABM.MortalType}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType}), Base.Iterators.Filter}

```

Returns active neighboring agents to given agent within euclidean distance `dist`. 
