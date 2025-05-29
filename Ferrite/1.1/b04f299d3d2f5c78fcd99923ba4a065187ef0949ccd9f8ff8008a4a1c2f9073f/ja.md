```
CellIterator(grid::Grid, cellset=1:getncells(grid))
CellIterator(dh::AbstractDofHandler, cellset=1:getncells(dh))
```

`CellIterator`を作成して、グリッド内のすべてのセルまたはそのサブセットを便利に反復処理します。イテレータの要素は、適切に`reinit!`初期化された[`CellCache`](@ref)です。詳細については[`CellCache`](@ref)を参照してください。

`CellIterator`をループすること、すなわち：

```julia
for cc in CellIterator(grid, cellset)
    # ...
end
```

は、次の同等のスニペットの単なる便利な方法です：

```julia
cc = CellCache(grid)
for idx in cellset
    reinit!(cc, idx)
    # ...
end
```

!!! warning
    `CellIterator`は状態を持ち、`for`ループ以外の目的（例えば、ブロードキャストやイテレータの収集）には使用すべきではありません（予期しない結果をもたらす可能性があります）。

