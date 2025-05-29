```
sort_into_targets!(target, source, stats) -> target, source, agg_stats
```

Aggregate coefficients from `source` to `target` and from `stats` to `agg_stats` according to thread- or MPI-level parallelism.

Returns the new `target` and `source`, as the sorting process may involve swapping them.
