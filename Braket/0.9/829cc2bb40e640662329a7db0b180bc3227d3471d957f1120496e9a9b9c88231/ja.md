```
AwsQuantumTaskBatch(device_arn::String, task_specs::Vector{<:Union{AbstractProgram, Circuit}}; kwargs...) -> AwsQuantumTaskBatch
```

`device_arn`で指定された`task_specs`による同時タスクのバッチを起動します。

有効な`kwargs`は次のとおりです：

  * `s3_destination_folder::Tuple{String, String}` - 結果を保存するs3バケットとプレフィックス。デフォルト：`default_task_bucket()`
  * `shots::Int` - 各タスクを実行するショットの数。デフォルト：1000
  * `poll_timeout_seconds::Int` - 結果をポーリングする間に待機する最大秒数。デフォルト：432000
  * `poll_interval_seconds::Int` - 結果をポーリングする間の試行間で待機するデフォルトの秒数。デフォルト：1
