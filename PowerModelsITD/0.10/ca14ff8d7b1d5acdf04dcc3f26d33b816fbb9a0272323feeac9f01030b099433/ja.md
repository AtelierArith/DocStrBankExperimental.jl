```
function resolve_units!(
    data::Dict{String,<:Any};
    multinetwork::Bool=false,
    number_multinetworks::Int=0
)
```

異なるデータセット全体で使用される単位を解決するために、同じ設定ベースを設定します。`data`は単位を解決することによって修正されるpmitd辞書であり、`multinetwork`は修正が必要な複数のネットワークがあるかどうかを定義するブール値であり、`number_multinetworks`はマルチネットワークの数を定義します。
