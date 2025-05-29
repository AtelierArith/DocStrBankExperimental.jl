```julia
create_similar(
    agent::EasyABM.GraphAgent{S<:EasyABM.MType, T<:EasyABM.MType}
) -> EasyABM.GraphAgent

```

`agent`と同じ（_extrasを除く）プロパティを持つn個の2次元エージェントのリストを返します。  
