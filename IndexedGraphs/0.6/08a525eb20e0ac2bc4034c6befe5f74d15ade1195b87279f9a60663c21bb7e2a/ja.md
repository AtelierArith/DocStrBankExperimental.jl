```
vertex(g::BipartiteIndexedGraph, i::Integer)
```

線形インデックス `i` に対応する [`BipartiteGraphVertex`](@ref) を構築します。`i` が `g` の頂点の範囲にない場合はエラーをスローします。
