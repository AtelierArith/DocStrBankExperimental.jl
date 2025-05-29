```
get_table_val(data, table_name, col_name, row_idx) -> val
```

Returns the value of the table at column `col_name` and row `row_idx`

Related functions:

  * [`get_table_num(data, table_name, col_name, row_idx, yr_idx, hr_idx)`](@ref): retrieves the `Float64` from `data[variable_name]`, indexing by year and hour.
  * [`get_num(data, name, yr_idx, hr_idx)`](@ref): retrieves a `Float64` from `data`, indexing by year and hour.
  * [`get_val(data, variable_name)`](@ref): retrieves the value from data[variable_name] regardless of type, not indexed by row, year or hour.
