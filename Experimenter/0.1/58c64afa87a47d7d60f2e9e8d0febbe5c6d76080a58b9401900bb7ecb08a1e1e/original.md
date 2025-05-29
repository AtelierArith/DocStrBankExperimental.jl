```
get_results_from_trial_global_database(trial_id::UUID)
```

Gets the results of a specific trial from the global database. Redirects to the master node if on a worker node. Locks to secure access.
