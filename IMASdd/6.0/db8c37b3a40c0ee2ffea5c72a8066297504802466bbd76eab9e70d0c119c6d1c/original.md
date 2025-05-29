```
new_timeslice!(@nospecialize(ids::IDS), time0::Float64=global_time(ids))
```

Recursively appends a deepcopy at time `time0` of the last time-slice of all time-dependent array structures under a given ids
