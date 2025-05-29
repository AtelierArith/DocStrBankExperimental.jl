```
ParallelModel(f::Function, name::Symbol)
```

The  `ParallelModel`  does what the `Model` does with a small difference. The function `f` is passed a `DataFrameRow` not the full `DataFrame`. If workers (through `Distributed`) are present, the rows are evaluated in parallel.
