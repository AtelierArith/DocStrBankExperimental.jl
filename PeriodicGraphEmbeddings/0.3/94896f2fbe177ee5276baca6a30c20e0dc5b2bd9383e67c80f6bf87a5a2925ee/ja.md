```
PeriodicGraphEmbedding{D,T}(pge::PeriodicGraphEmbedding{N,S}) where {D,T,N,S}
PeriodicGraphEmbedding{D}(pge::PeriodicGraphEmbedding{N,S}) where {D,N,S}
```

入力 `pge` と同じ構造情報を持つ [`PeriodicGraphEmbedding{D,T}`](@ref) を返しますが、`N` 次元の代わりに `D` 次元に埋め込まれます。

`T` が指定されていない場合は、`S` にデフォルト設定されます。

`PeriodicGraph{D}(graph::PeriodicGraph{N})` に適用されるのと同じ注意点がここでも有効です。すなわち、グラフの次元は少なくとも `D` である必要があり、`D < N` で非同一の接続成分が複数ある場合は動作が未定義になります。

さらに、`D < N` の場合、すべての頂点の最後の `N-D` 座標はゼロでなければならず、そうでない場合はこの関数はエラーになります。
