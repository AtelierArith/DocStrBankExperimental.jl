```
bellman_ford_shortest_paths(g, s, distmx=weights(g))
bellman_ford_shortest_paths(g, ss, distmx=weights(g))
```

ソース `s`（またはソースのリスト `ss`）とグラフ `g` のすべての他のノードとの間の最短経路を [ベルマン-フォードアルゴリズム](http://en.wikipedia.org/wiki/Bellman–Ford_algorithm) を使用して計算します。

関連するトラバーサル情報を持つ [`Graphs.BellmanFordState`](@ref) を返します（`state.parents` または `state.dists` をクエリしてみてください）。
