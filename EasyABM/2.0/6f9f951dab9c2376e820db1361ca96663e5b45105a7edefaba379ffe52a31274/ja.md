```julia
agent_with_id(
    i::Int64,
    model::EasyABM.SpaceModel3D{EasyABM.StaticType}
) -> Union{Nothing, EasyABM.Agent3D{S, P, EasyABM.StaticType} where {S<:Union{Float64, Int64}, P<:EasyABM.SType}}

```

指定されたIDを持つエージェントを返します。
