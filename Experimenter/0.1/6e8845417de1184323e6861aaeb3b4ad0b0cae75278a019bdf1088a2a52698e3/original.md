```
complete_trial_in_global_database(trial_id::UUID, results::Dict{Symbol,Any})
```

Marks a specific trial (with `trial_id`) complete in the global database and stores the supplied `results`. Redirects to the master node if on a worker node. Locks to secure access.
