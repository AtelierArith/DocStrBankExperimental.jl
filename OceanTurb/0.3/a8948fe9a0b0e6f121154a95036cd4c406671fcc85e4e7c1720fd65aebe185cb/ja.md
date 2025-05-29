```
CellField(data, grid)
```

`grid`上に`data`が配置された`CellField`を返します。もし`data`が`CellField`の*合計*サイズと同じであれば、`data`は`OffsetArray`にラップされます。それ以外の場合、`data`は`size(grid)`の`CellField`に設定可能でなければなりません。
