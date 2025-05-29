```
PartialCellBottom(bottom_height; minimum_fractional_cell_height=0.2)
```

`PartialCellBottom`は、「部分的な」底セルを持つ浸漬境界を表します。つまり、各列の最下部セルの高さは、提供された`bottom_height`に合わせて減少します。これは`Field`、`Array`、または`(x, y)`の関数である可能性があります。

部分的な底セルの高さは次のより大きいです。

```
minimum_fractional_cell_height * Δz,
```

ここで、`Δz`は基盤グリッドの底セルの元の高さです。
