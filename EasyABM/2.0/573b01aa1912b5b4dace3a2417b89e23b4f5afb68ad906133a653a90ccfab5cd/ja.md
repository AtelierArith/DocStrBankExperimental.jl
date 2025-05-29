```julia
create_similar(
    agent::EasyABM.Agent2D{S<:Union{Float64, Int64}, P<:EasyABM.SType, T<:EasyABM.MType},
    n::Int64
) -> Array{EasyABM.Agent2D{S, P, T}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType, T<:EasyABM.MType}

```

`agent`が生きている場合、`agent`と同じ（_extrasを除く）プロパティを持つn個の2Dエージェントのリストを返します。  
