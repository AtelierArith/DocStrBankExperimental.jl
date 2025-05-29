```
field(A, indices)
field(A, fieldname)
```

セル配列 `A` のフィールドを `indices` または `fieldname` で指定して配列ビューを返します（ビューを変更すると `A` も変更されます）。ビューの次元とサイズは `A` と等しいです。パラメータ `B` が `0` でも `1` でもない場合、この操作はサポートされていません。

## 引数

  * `indices::Int|NTuple{N,Int}`: `A` のセルタイプに従ってフィールドを指定する `indices`（多次元セルの場合はフラットインデックスがサポートされています）。
  * `fieldname::Symbol`: `A` のセルタイプに従ってフィールドを指定する `fieldname`。
