```
get_edge_data(g::BipartiteFactorGraph{TVar,TFac,E}, v1::Int, v2::Int) where {TVar,TFac,E}
```

ノード `v1` と `v2` の間のエッジに関連付けられたデータを取得します。グラフは無向であるため、`v1` と `v2` の順序は重要ではありません。
