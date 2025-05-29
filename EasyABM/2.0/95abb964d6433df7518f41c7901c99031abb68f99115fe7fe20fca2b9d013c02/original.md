```julia
agent_with_id(
    i::Int64,
    model::EasyABM.SpaceModel2D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType}
) -> Union{Nothing, EasyABM.Agent2D{S, P, EasyABM.MortalType} where {S<:Union{Float64, Int64}, P<:EasyABM.SType}}

```

Returns agent having given id.
