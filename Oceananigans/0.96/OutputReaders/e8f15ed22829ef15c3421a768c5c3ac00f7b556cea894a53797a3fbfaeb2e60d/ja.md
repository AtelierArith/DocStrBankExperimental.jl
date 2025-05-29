```
FieldTimeSeries{LX, LY, LZ}(grid::AbstractGrid [, times=()]; kwargs...)
```

`grid` と `times` に対して `FieldTimeSeries` を構築します。

# キーワード引数

  * `indices`: 空間インデックス
  * `backend`: バックエンド、`InMemory(indices=Colon())` または `OnDisk()`
  * `path`: `backend = OnDisk()` のデータへのパス
  * `name`: `backend = OnDisk()` のフィールド名
