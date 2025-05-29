```
timeline(;t_start::Real=0., t_end::Real, step::Real=(t_end - t_start)/250.)
```

Generate `RheoTimeData` struct with only the time data based on the keywords provided.

# Arguments

  * `t_start`: Starting time, typically 0
  * `t_end`: End time
  * `step`: Time between sample. Default set in order to provide ≈ 250 time points.
