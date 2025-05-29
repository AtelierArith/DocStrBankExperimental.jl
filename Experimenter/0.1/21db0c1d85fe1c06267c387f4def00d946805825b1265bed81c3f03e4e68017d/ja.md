```
complete_trial!(db::ExperimentDatabase, trial_id::UUID, results::Dict{Symbol,Any})
```

データベース内の特定のトライアル（`trial_id`）を完了としてマークし、提供された`results`を保存します。
