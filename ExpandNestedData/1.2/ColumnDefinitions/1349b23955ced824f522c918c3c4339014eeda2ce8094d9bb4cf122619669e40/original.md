```
ColumnDefinition(field_path; column_name=nothing, flatten_arrays=false, default_value=missing, pool_arrays=false)
```

## Args

  * `field_path`: Vector or Tuple of keys/fieldnames that constitute a path from the top of the data to the values to extract for the column

## Keyword Args

  * `column_name::Symbol`: A name for the resulting column. If `nothing`, defaults to joining the `field_path` with snake case format.
  * `default_value`: When the field_path keys do not exist on one or more branches, fill with this value. Default: `missing`
  * `pool_arrays::Bool`: When collecting values for this column, choose whether to use `PooledArrays` instead of `Base.Vector`. Default: `false` (use `Vector`)
  * `name_join_pattern::String`: The separator for joining field paths into column names. Default: "_"

## Returns

`::ColumnDefinition`
