```
trace = draw_orbit(orb, starttime, endtime=nothing; kwargs...)
```

Creates a vector of traces of an orbit `orb` at each true anomaly in `angles`.

When both a start time and end time are provided, the orbit is drawn between the two times. If the end time is not specified, a full period is drawn. 
