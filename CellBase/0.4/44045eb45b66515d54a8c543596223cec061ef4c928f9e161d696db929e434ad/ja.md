```
Cell(cell::SCell)
```

`Spglib.Cell` から `Cell` オブジェクトを返します。ここで、`SCell.types` は 1 ベースのインデックスに変更されています。これは、`Spglib._expand_cell` が呼び出されるときに、返される `types` が再インデックスされるため便利です。
