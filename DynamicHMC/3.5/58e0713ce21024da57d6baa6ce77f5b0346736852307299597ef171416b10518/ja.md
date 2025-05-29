```julia
struct LogProgressReport{T}
```

`Logging` フレームワークに進捗を報告し、`@info` を使用します。

報告される情報において、*ステップ* は NUTS 遷移であり、リープフロッグステップではありません。

# フィールド

  * `chain_id`: チェーンの ID。任意のオブジェクトで構いません。例: `nothing`。
  * `step_interval`: 最後の報告から `step_interval` を超えた進捗を常に報告します。
  * `time_interval_s`: 最後の報告からこの時間（秒単位）を超えた進捗を常に報告します。
