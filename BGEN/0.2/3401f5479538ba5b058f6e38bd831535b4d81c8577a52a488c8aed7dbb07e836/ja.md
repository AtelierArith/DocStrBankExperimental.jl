```
Bgen(path; sample_path=nothing, delay_parsing=false)
```

Bgenファイル情報を読み込みます：ヘッダー、サンプルのリスト。バリアントとジェノタイプは別々に読み込まれます。

  * `path`: ".bgen"ファイルへのパス。
  * `sample_path`: 該当する場合の".sample"ファイルへのパス。
  * `idx_path`: ".bgi"ファイルへのパス、デフォルトは`path * ".bgi"`です。
