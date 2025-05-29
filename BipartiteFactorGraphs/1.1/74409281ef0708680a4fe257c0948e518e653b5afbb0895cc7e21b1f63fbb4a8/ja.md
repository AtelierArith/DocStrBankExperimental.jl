```
edges(g::BipartiteFactorGraph)
```

グラフ内のすべてのエッジを取得します。

!!! note
    この関数は `variables` や `factors` とは異なり、`Graphs.edges` を呼び出します。 ノードに対する最も近い同等物は `neighbors` 関数です。

