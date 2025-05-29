```
save_snapshot!(db::ExperimentDatabase, trial_id::UUID, state::Dict{Symbol,Any}, [label])
```

指定された `state` をデータベースに保存し、一致する `trial_id` を持つトライアルに関連付けます。スナップショットの時間が自動的に保存されます。
