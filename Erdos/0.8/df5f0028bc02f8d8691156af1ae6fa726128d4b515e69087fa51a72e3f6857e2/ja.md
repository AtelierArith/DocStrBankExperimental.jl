```
bellman_ford_shortest_paths(g, s, distmx=weights(g))
bellman_ford_shortest_paths(g, sources, distmx=weights(g))
```

`g`のソース頂点`s`（またはソース頂点のセット`sources`）からのすべての頂点の最短経路を計算するために、[ベルマン-フォードアルゴリズム](http://en.wikipedia.org/wiki/Bellman–Ford_algorithm)を使用します。関連するトラバーサル情報を持つ`BellmanFordState`を返します。
