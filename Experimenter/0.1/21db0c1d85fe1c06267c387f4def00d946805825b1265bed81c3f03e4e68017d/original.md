```
complete_trial!(db::ExperimentDatabase, trial_id::UUID, results::Dict{Symbol,Any})
```

Marks a specific trial (with `trial_id`) complete in the database and stores the supplied `results`.
