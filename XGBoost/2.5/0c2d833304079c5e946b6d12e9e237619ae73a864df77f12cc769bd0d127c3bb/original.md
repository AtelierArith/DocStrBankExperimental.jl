```
importancetable(b::Booster)
```

Return a Table.jl compatible table (named tuple of `Vector`s) giving a summary of all available feature importance statistics for `b`.  This table is mainly intended for display purposes, see [`importance`](@ref) for a more direct way of retrieving importance statistics. See [`importancereport`](@ref) for a convenient display of this table.
