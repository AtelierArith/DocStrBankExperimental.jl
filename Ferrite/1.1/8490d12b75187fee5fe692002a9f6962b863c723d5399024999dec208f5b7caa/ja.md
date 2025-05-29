```
InterfaceIterator(grid::Grid, [topology::ExclusiveTopology])
InterfaceIterator(dh::AbstractDofHandler, [topology::ExclusiveTopology])
```

`InterfaceIterator`を作成して、グリッド内のすべてのインターフェースを便利に反復処理します。イテレータの要素は、適切に`reinit!`初期化された[`InterfaceCache`](@ref)です。詳細については[`InterfaceCache`](@ref)を参照してください。`InterfaceIterator`をループすること、すなわち：

```julia
for ic in InterfaceIterator(grid, topology)
    # ...
end
```

は、次の同等のスニペットの単なる便利な方法です（次元が1より大きいグリッドの場合）：

```julia
ic = InterfaceCache(grid)
neighborhood = Ferrite.get_facet_facet_neighborhood(topology, grid)
for facet in facetskeleton(topology, grid)
    neighbors = neighborhood[facet[1], facet[2]]
    isempty(neighbors) && continue
    neighbor_facet = neighbors[1]
    reinit!(ic, facet, neighbor_facet)
    # ...
end
```

!!! warning
    `InterfaceIterator`は状態を持ち、`for`ループ以外の目的（例えば、ブロードキャストやイテレータの収集）には使用すべきではありません。予期しない結果をもたらす可能性があります。

