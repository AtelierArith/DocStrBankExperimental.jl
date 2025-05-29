```
a_star(g, s, t[, distmx][, heuristic])
```

頂点 `s` と `t` の間の最短経路を構成するエッジのベクトルを返します。これは [A* 探索アルゴリズム](http://en.wikipedia.org/wiki/A%2A_search_algorithm) を使用しています。オプションのヒューリスティック関数とエッジ距離行列を指定することができます。指定しない場合、距離行列は [`LightGraphs.DefaultDistance`](@ref) に設定され、ヒューリスティックは `n -> 0` に設定されます。
