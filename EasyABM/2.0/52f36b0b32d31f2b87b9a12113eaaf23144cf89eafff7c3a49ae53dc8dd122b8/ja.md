```julia
add_agent!(
    agent,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.StaticType, EasyABM.MortalType}}
) -> Union{Nothing, Int64}

```

モデルにエージェントを追加します。
