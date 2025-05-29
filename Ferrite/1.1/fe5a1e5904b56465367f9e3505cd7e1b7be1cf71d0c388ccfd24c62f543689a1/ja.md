```
collect_periodic_facets(grid::Grid, all_facets::Union{AbstractSet{FacetIndex},String,Nothing}=nothing; tol=1e-12)
```

`all_facets`内のすべてのファセットを画像セットとミラーセットに分割します。各一致するペアについて、ベクトル `(1, 1, 1)` に沿ってさらに位置するファセットが画像ファセットになります。

セットが指定されていない場合、グリッドの外部境界上のすべてのファセット（すなわち、隣接するファセットを持たないすべてのファセット）が使用されます。

参照: [`collect_periodic_facets!`](@ref), [`PeriodicDirichlet`](@ref).
