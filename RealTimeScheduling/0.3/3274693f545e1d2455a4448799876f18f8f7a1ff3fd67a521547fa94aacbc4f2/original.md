```
schedule_gedf(T, m, time; kill=false)
```

Simulate a preemptive global earliest-deadline-first (GEDF) schedule of task system `T` on `m` processors for the specified `time`.

If `kill` is `true`, jobs are killed at their deadline if they have not yet completed.

See also [`schedule_global`](@ref) for more general global scheduling.
