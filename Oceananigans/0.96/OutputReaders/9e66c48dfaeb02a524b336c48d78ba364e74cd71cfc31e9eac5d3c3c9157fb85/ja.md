```
FieldDataset(filepath;
             architecture=CPU(), grid=nothing, backend=InMemory(), metadata_paths=["metadata"])
```

指定された `filepath` にある JLD2 ファイル内の各フィールドに対する `FieldTimeSeries` を含む `Dict` を返します。モデルの出力は **必ず** ハローと共に保存されている必要があります。

# キーワード引数

  * `backend`: `InMemory()`（デフォルト）または `OnDisk()` のいずれか。`InMemory` バックエンドはデータを完全にメモリに読み込み、4D 多次元配列として扱いますが、`OnDisk()` バックエンドは `FieldTimeSeries` が線形にインデックス付けされるときにフィールドの時間スナップショットを遅延読み込みします。
  * `metadata_paths`: メタデータを探すための JLD2 パスのリスト。デフォルトでは `file["metadata"]` を参照します。
  * `grid`: JLD2 ファイルで使用されるグリッドを上書きするために指定できます。
  * `reader_kw`: ファイルを開くときに使用するリーダー（現在は JLD2 のみ）に渡すキーワード引数の名前付きタプルまたは辞書。
