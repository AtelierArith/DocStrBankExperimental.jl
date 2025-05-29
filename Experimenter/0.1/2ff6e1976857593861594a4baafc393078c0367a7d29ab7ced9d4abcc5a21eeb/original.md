```
save_snapshot!(db::ExperimentDatabase, trial_id::UUID, state::Dict{Symbol,Any}, [label])
```

Saves the snapshot with given `state` in the database, associating with the trial with matching `trial_id`. Automatically saves the time of the snapshot.
