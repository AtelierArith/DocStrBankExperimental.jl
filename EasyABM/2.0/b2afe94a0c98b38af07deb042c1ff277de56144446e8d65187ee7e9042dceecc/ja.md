```julia
agent_with_id(
    i::Int64,
    model::EasyABM.SpaceModel2D{EasyABM.StaticType}
) -> Union{Nothing, EasyABM.Agent2D{S, P, EasyABM.StaticType} where {S<:Union{Float64, Int64}, P<:EasyABM.SType}}

```

指定されたIDを持つエージェントを返します。
