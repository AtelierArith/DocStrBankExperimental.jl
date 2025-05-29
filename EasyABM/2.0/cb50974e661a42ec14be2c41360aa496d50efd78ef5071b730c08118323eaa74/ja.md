```julia
add_nodes!(
    n,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}};
    kwargs...
)

```

モデルのグラフに`kwargs`で指定されたプロパティを持つnノードを追加します。
