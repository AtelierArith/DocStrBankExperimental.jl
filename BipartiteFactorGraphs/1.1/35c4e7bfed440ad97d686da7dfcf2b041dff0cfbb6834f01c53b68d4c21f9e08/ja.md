```
factor_neighbors(g::BipartiteFactorGraph, v::Int)
```

変数ノード v のすべての因子隣接ノードを取得します。因子ノードのみが隣接ノードとして返されます。この関数は、ノードが変数であることを確認する追加のチェックを行う `neighbors(g, v)` と同等です。ノードタイプをチェックしないバージョンが必要な場合は、`neighbors(g, v)` を使用してください。
