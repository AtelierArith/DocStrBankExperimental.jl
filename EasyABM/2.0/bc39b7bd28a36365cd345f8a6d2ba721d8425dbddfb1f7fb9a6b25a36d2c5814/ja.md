```julia
create_similar(
    agent::EasyABM.GraphAgent{S<:EasyABM.MType, T<:EasyABM.MType},
    n::Int64
) -> Array{EasyABM.GraphAgent{S, T}, 1} where {S<:EasyABM.MType, T<:EasyABM.MType}

```

`agent`と同じ（_extrasを除く）プロパティを持つn個の2dエージェントのリストを返します。  
