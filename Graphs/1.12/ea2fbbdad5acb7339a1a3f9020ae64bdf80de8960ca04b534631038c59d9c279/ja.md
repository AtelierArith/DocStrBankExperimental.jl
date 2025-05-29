```
floyd_warshall_shortest_paths(g, distmx=weights(g))
```

[Floyd-Warshallアルゴリズム](http://en.wikipedia.org/wiki/Floyd–Warshall_algorithm)を使用して、グラフ`g`内のすべての頂点のペア間の最短経路を計算します。オプションの距離行列`distmx`を使用します。関連するトラバーサル情報を持つ[`Graphs.FloydWarshallState`](@ref)を返します（`state.parents`や`state.dists`をクエリしてみてください）。

### パフォーマンス

空間の複雑さは`O(|V|^2)`のオーダーです。
