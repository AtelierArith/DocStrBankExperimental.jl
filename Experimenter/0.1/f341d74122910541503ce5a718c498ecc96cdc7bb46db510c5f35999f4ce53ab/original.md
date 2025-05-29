```
mark_trial_as_incomplete!(db::ExperimentDatabase, trial_id)
```

Marks a specific trial (with `trial_id`) as incomplete, which means it will run again from scratch upon the next execution.
