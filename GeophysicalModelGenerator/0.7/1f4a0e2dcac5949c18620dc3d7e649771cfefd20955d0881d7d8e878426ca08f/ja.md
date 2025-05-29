```
FEData{dim, points_per_cell}
```

頂点およびセルデータを持つ有限要素情報を保持する構造体。任意の要素に対して2D/3Dで動作します。

# パラメータ

  * メッシュ上の点を持つ `vertices` （`dim` x `Npoints`）
  * メッシュの接続性を持つ `connectivity` （`points_per_cell` x `Ncells`）
  * 頂点上のフィールドを持つ `fields`
  * セルのフィールドを持つ `cellfields`
