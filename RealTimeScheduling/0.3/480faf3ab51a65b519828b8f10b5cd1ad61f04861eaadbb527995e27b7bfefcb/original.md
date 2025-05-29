```
schedule_gfl(T, m, time; kill=false)
```

Simulate a preemptive global fair lateness (GFL) schedule of task system `T` on `m` processors for the specified `time`.  This provides the lowest tardiness bounds of any GEDF-like scheduler under compliant vector analysis; for more information, see Erickson, "Managing Tardiness Bounds and Overload in Soft Real-Time Systems." DOI: [10.17615/fvp3-q039](https://doi.org/10.17615/fvp3-q039).

If `kill` is `true`, jobs are killed at their deadline if they have not yet completed.

See also [`schedule_global`](@ref) for more general global scheduling.
