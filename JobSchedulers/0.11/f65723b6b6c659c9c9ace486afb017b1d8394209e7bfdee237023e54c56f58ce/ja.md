```
all_queue()
all_queue(id::Integer)
all_queue(state::Symbol)
all_queue(needle::Union{AbstractString,AbstractPattern,AbstractChar})
```

  * `state::Symbol`: 特定の状態のジョブを取得します。状態には `:all`, `QUEUING`, `RUNNING`, `DONE`, `FAILED`, `CANCELLED`, `PAST` が含まれます。

    > `PAST` は `DONE`, `FAILED`, `CANCELLED` のスーパーセットです。
  * `needle::Union{AbstractString,AbstractPattern,AbstractChar}`: 名前またはユーザーに `needle` を含むジョブを取得します。
  * `id::Integer`: 特定の `id` を持つジョブを取得します。
