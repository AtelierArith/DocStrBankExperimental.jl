```
evaluate!(m::Model, df::DataFrame)
```

Calls `m.func` with `df` and adds the result to the `DataFrame` as a column `m.name`
