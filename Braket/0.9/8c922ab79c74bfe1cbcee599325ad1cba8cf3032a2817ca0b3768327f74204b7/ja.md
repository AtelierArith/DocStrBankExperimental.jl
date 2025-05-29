```
results(b::AwsQuantumTaskBatch; kwargs)
```

有効な `kwargs` は次のとおりです：

  * `fail_unsuccessful::Bool` - リトライ後にバッチ内のタスクが失敗した場合にエラーをスローするかどうか。デフォルト：`false`
  * `max_retries::Int` - 失敗したタスクをリトライする最大回数。デフォルト：3
  * `use_cached_value::Bool` - タスクのために以前にダウンロードした結果を再利用するか、すべての結果を新たにダウンロードするかどうか。デフォルト：`true`

`b` のすべてのタスクの結果を取得する間、ブロックして待機します。
