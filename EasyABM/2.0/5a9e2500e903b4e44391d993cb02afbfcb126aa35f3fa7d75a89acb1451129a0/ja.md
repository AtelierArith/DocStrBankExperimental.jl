```julia
create_similar(
    agent::EasyABM.Agent2D{S<:Union{Float64, Int64}, P<:EasyABM.SType, T<:EasyABM.MType}
) -> EasyABM.Agent2D

```

与えられた `agent` と同じ（_extras を除く）プロパティを持つエージェントを返します。
