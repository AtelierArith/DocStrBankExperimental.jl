```
write(ds::Dataset, df::DataFrame)
```

Writes a `DataFrame` via `CSV.write` to a filepath defined by the `Dataset` type.

*NOTE:* A prefect server must be available to use Dataset read function.
