```
timerange = TimeRange(t_start, t_end)
```

The `TimeRange` function is a custom constructor for the `TimeCurve` struct.  It allows defining a simple time interval, with start and end times.

# Arguments

  * `t_start`: (`::Real`, `[s]`, `=0.0`) start time
  * `t_end`: (`::Real`, `[s]`, `=1.0`) end time

# Returns

  * `timerange`: (`::TimeCurve`) TimeCurve struct

# Examples

```julia-repl
julia> timerange = TimeRange(t_start=0.6, t_end=1.4)
```

![Time Range](../assets/time-range.svg)
