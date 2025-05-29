```
johnson_shortest_paths(g, distmx=weights(g))
```

グラフ `g` のすべての頂点間の最短経路を計算するために、オプションの距離行列 `distmx` を使用して [ジョンソンアルゴリズム](https://en.wikipedia.org/wiki/Johnson%27s_algorithm) を使用します。

関連するトラバーサル情報を持つ [`Graphs.JohnsonState`](@ref) を返します（`state.parents` または `state.dists` をクエリしてみてください）。

### パフォーマンス

複雑さ: `O(|V|*|E|)`
