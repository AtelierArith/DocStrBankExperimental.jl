```julia
neighbors(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType}
) -> Union{Base.Generator{I, typeof(identity)} where I<:(Array{EasyABM.Agent2D{S, P, EasyABM.MortalType}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType}), Base.Iterators.Filter}
neighbors(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType},
    dist::Real
) -> Union{Base.Generator{I, typeof(identity)} where I<:(Array{EasyABM.Agent2D{S, P, EasyABM.MortalType}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType}), Base.Iterators.Filter}

```

Returns active neighboring agents to given agent within euclidean distance `dist`. 
