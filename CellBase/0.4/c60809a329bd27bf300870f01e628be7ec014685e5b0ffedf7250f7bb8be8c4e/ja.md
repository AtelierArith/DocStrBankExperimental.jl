```
ExtendedPointArray(cell::Cell, rcut)
```

与えられた構造からExtendedPointArrayを構築します。暗黙的に、位置は単位セル内にラップされており、元のCellの実際の位置が単位セルの外にあっても同様です。これにより、正しい隣接リストが構築されることが保証されます。
