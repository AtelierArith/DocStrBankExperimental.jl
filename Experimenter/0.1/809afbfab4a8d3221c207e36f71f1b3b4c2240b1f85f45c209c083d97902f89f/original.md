```
get_latest_snapshot_from_global_database(trial_id::UUID)
```

Same as `get_latest_snapshot`, but in the given global database. Redirects to the master worker if on a distributed node. Only works when using `@execute`.
