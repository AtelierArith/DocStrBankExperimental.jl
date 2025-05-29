```
mark_trial_as_incomplete!(db::ExperimentDatabase, trial_id)
```

特定のトライアル（`trial_id`を持つ）を未完了としてマークします。これは、次回の実行時に最初から再実行されることを意味します。
