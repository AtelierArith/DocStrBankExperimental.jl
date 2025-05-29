```
ValOutDiGraph{V = Int32}(n; vertexval_types=(), edgeval_types=(), vertexval_init=nothing, graphvals=())
ValOutDiGraph{V, V_VALS, E_VALS}(n; vertexval_init=nothing, graphvals=())
```

`n` 頂点、ゼロエッジ、グラフ値 `graphvals` を持つ `ValOutDiGraph` を構築します。 頂点値の型は `V_VALS` または `vertexval_types` のいずれかであり、エッジ値の型は `edgeval_types` です。

省略された場合、要素型 `V` は Int32 です。
