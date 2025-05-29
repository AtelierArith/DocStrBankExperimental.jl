```
get_table_row_idxs(data, table_name, conditions...) -> row_idxs::Vector{Int64}
```

Gets the row indices for `data[table_name]` for which the `conditions` hold true.  See [`get_table`](@ref) for a description of possible conditions
