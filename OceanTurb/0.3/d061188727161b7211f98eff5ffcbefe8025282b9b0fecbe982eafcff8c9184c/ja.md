```
arraytype(grid::Grid)
```

`grid`上に存在するデータに対応する配列型を返します。デフォルトは`Array`です。新しいデータ型（例えば、GPU上に存在するグリッド）は新しい配列型を実装する必要があります。
