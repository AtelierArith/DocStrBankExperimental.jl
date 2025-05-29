```
result(j::AwsQuantumJob; kwargs...)
```

ジョブ `j` の結果をダウンロード、抽出、およびデシリアライズします。有効な `kwargs` は次のとおりです：

  * `poll_timeout_seconds::Int` - 結果をポーリングする間に待機する最大秒数。デフォルト：864000
  * `poll_interval_seconds::Int` - ダウンロード試行の間に待機する秒数。デフォルト：5
