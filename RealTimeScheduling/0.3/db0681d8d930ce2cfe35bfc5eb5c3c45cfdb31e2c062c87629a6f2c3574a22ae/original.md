```
schedule_gfp(T, m, time; kill=false)
```

Simulate a preemptive global fixed priority (GFP) schedule of task system `T` on `m` processors for the specified `time`.  Tasks are prioritized by their index in `T`, lowest index first.

If `kill` is `true`, jobs are killed at their deadline if they have not yet completed.

See also [`schedule_global`](@ref) for more general global scheduling.
