```julia
struct ProgressReport{P<:BaytesCore.ProgressLog, K}
```

サンプリングプロセス中のサンプリング出力をログするためのデフォルト引数。

# フィールド

  * `bar::Bool`: サンプリング実行中にプログレスバーが有効かどうかのブール値
  * `log::BaytesCore.ProgressLog`: 出力診断を印刷するべきかどうかのブール値。
  * `kwargs::Any`: 出力を返すために使用される追加のProgressMeterキーワード
