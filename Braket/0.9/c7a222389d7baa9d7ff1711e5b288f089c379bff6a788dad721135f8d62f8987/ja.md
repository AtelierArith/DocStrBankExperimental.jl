```
logs(j::AwsQuantumJob; wait::Bool=false, poll_interval_seconds::Int=5)
```

ジョブ `j` のログを取得します。`wait` が `true` の場合、`j` が端末状態（`"COMPLETED"`、`"FAILED"`、または `"CANCELLED"`）に入るまでブロックします。新しいログデータのために毎 `poll_interval_seconds` ごとにポーリングします。
