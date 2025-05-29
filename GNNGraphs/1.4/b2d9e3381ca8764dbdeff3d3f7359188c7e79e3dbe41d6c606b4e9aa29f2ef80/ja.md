```
remove_multi_edges(g::GNNGraph; aggr=+)
```

グラフ `g` から複数のエッジ（平行エッジまたは繰り返しエッジとも呼ばれる）を削除します。可能なエッジの特徴は `aggr` に従って集約され、`+`、`min`、`max`、または `mean` の値を取ることができます。

[`remove_self_loops`](@ref)、[`has_multi_edges`](@ref)、および [`to_bidirected`](@ref) も参照してください。
