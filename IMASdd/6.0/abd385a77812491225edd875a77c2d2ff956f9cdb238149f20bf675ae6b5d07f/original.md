```
get_timeslice(@nospecialize(ids::IDS), time0::Float64=global_time(ids), scheme::Symbol=:constant; slice_pulse_schedule::Bool=true)
```

Returns data at the given `time0` (by default at the global_time)

Data is selected from time dependent arrays of structures using closest causal time point.

Data is selected from time dependent arrays using these possible schemes `[:constant, :linear, :quadratic, :cubic, :pchip, :lagrange]`
