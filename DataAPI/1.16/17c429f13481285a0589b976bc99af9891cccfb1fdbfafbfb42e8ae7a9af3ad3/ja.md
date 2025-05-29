```
deletecolmetadata!(x, col, key::AbstractString)
```

テーブル `x` の列 `col` に対するキー `key` のメタデータを削除し、`x` を返します（`key` のメタデータが存在しない場合は何も行いません）。列 `col` に対するメタデータの削除を `x` がサポートしていない場合はエラーをスローします。
