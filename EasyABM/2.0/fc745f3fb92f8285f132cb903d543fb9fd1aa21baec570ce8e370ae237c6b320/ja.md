```julia
agent_with_id(
    i::Int64,
    model::EasyABM.SpaceModel3D{EasyABM.MortalType, S<:Union{Float64, Int64}, P<:EasyABM.SType}
) -> Union{Nothing, EasyABM.Agent3D{S, P, EasyABM.MortalType} where {S<:Union{Float64, Int64}, P<:EasyABM.SType}}

```

指定されたIDを持つエージェントを返します。
