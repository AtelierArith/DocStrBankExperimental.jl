```julia
kill_edge!(
    edge,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}}
) -> Union{Nothing, EasyABM.PropDataDict{Symbol, Any}}

```

モデルグラフからエッジを削除します。
