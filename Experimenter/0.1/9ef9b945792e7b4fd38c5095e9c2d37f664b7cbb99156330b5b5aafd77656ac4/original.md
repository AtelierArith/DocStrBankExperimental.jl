```
latest_snapshot(db::ExperimentDatabase, trial_id)
```

Gets the latest snapshot from the database for a given trial with matching `trial_id`, using the date of the most recent snapshot.

Known to have issues when snapshots are created within the same second.
