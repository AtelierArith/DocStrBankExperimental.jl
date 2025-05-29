```julia
add_node!(
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}};
    kwargs...
) -> Int64

```

モデルのグラフに`kwargs`で指定されたプロパティを持つノードを追加します。
