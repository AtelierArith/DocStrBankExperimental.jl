```
complete_trial_in_global_database(trial_id::UUID, results::Dict{Symbol,Any})
```

特定のトライアル（`trial_id`）をグローバルデータベースで完了としてマークし、提供された`results`を保存します。ワーカーノードにいる場合はマスターノードにリダイレクトします。アクセスを保護するためにロックします。
