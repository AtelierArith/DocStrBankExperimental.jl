```
save_snapshot_in_global_database(trial_id::UUID, state, [label])
```

Save the results of a specific trial from the global database, with the supplied `state` and optional `label`. Redirects to the master node if on a worker node. Locks to secure access.
