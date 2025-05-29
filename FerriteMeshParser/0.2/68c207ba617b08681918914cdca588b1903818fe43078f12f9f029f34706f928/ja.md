```
create_facetset(
    grid::Ferrite.AbstractGrid, 
    nodeset::Set{Int}, 
    cellset::Union{UnitRange{Int},Set{Int}}=1:getncells(grid)
    )
```

グリッド内のすべてのノードが `nodeset` に含まれるファセットを見つけます。それらを `Set{FacetIndex}` として返します。計算を高速化するために、特定のセルの間の面のみを探すために `cellset` を指定することができます。そうでなければ、すべてのセルを対象に検索が行われます。

この関数は通常、`generate_facetsets=false` で `get_ferrite_grid` を呼び出すときにのみ必要です。作成された `facetset` は、`addfacetset!(grid, "facetsetkey", facetset)` としてグリッドに追加できます。
