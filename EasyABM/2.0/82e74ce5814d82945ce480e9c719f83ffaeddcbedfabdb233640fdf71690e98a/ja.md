```julia
create_similar(
    agent::EasyABM.Agent3D{S<:Union{Float64, Int64}, P<:EasyABM.SType, T<:EasyABM.MType}
) -> EasyABM.Agent3D

```

与えられた `agent` と同じプロパティを持つエージェントを返します。
