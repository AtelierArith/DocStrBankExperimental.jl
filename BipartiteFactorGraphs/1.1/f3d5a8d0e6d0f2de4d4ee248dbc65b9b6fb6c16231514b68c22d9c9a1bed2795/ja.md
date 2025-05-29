```
variable_neighbors(g::BipartiteFactorGraph, v::Int)
```

因子ノード v のすべての変数隣接ノードを取得します。変数ノードである隣接ノードのみを返します。この関数は、ノードが因子であることを確認する追加のチェックを行う `neighbors(g, v)` と同等です。ノードタイプをチェックしないバージョンが必要な場合は、`neighbors(g, v)` を使用してください。
