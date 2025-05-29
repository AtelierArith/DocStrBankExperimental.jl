```
DTable(table; tabletype=nothing) -> DTable
```

Constructs a `DTable` using a `Tables.jl`-compatible input `table`. Calls `partitions` on `table` and assumes the provided partitioning.
