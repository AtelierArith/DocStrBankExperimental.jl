```julia
create_edge!(
    i,
    j,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}};
    kwargs...
)

```

モデルグラフにプロパティ `kwargs` を持つエッジを追加します。
