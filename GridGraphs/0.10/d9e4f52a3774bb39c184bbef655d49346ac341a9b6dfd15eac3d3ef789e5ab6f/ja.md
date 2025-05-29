```
grid_topological_sort(g, s)
```

非循環 `GridGraph` `g` に対してトポロジカルソートを適用し、ソース `s` を持つ `ShortestPathTree` を返します。

頂点インデックスがトポロジカルランクに対応していると仮定します。ForwardDiff と互換性があります。
