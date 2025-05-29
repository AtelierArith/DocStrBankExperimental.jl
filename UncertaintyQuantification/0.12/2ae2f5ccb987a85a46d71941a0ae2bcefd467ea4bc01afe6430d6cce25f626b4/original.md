```
evaluate!(m::ParallelModel, df::DataFrame)
```

Calls `m.func` for each row of `df` and adds the result to the `DataFrame` as a column `m.name`. If workers are added through `Distributed`, the rows will be evaluated in parallel.
