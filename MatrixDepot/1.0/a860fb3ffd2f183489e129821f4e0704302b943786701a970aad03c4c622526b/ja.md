```
@pred(expression)
```

式を関数本体として使用して述語関数を生成します。式内の変数名は `RemoteMatrixData` のプロパティ（例：`title`、`m`、`nnz`）であり、`data.title` などにアクセスするために使用されます。他の変数名は外部スコープから使用されます。

例： `maxnnz = 1_000; listnames(@pred(n <= maxnnz))` は、`maxnnz` より少ない構造的非ゼロを持つすべてのデータのリストを生成します。
