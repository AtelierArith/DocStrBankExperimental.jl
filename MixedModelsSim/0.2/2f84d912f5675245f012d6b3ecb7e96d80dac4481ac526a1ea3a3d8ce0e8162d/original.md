```
pooled!(df, cols::Type=Union{AbstractString,Missing})
```

Like `DataFrames.categorical!` but converting columns to `PooledArray`s

!!! warning
    This method is not type-specific in the first argument, in order to eliminate a dependency on `DataFrames.jl`. It nonetheless expects a `DataFrame` as its first argument

