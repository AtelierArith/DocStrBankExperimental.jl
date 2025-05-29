```
DTable(table, chunksize; tabletype=nothing, interpartition_merges=true) -> DTable
```

Constructs a `DTable` using a `Tables.jl` compatible `table` input. It assumes no initial partitioning of the table and uses the `chunksize` argument to partition the table (based on row count).

Providing `tabletype` kwarg overrides the internal table partition type.

Using the `interpartition_merges` kwarg you can decide whether you want to opt out of merging rows between partitions. This option is enabled by default, which means it will prioritize creating chunks of the specified size even if it means taking rows from two or more partitions. When disabled there won't be any merges between partitions meaning several chunks can be smaller than expected due to shortage of rows within a partition. Please see tests for examples of behaviour.
