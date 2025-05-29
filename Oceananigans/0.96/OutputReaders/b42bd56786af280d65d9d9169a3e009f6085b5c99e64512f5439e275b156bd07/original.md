```
set!(fts::OnDiskFieldTimeSeries, field::Field, n::Int, time=fts.times[time_index])
```

Write the data in `parent(field)` to the file at `fts.path`, under `fts.name` and at `time_index`. The save field is assigned `time`, which is extracted from `fts.times[time_index]` if not provided.
