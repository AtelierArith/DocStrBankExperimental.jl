```
trim_time!(@nospecialize(ids::IDS), time_range::Tuple{Float64,Float64}; trim_pulse_schedule::Bool=false)
```

Recursively remove all time dependent data tha occurs outside of `time_range`
