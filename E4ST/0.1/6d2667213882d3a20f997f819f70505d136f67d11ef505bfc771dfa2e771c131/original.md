```
get_num(data, variable_name, yr_idx, hr_idx) -> num::Float64

get_num(table, col_name, row_idx, yr_idx, hr_idx) -> num::Float64
```

Retrieves a `Float64` from `data[variable_name]`, indexing by year and hour.  Works for [`Container`](@ref)s and `Number`s.

Related functions:

  * [`get_table_val(data, table_name, col_name, row_idx)`](@ref): retrieves the raw value from the table (without indexing by year/hour).
  * [`get_table_num(data, table_name, col_name, row_idx, yr_idx, hr_idx)`](@ref): retrieves the `Float64` from `data[variable_name]`, indexing by year and hour.
  * [`get_val(data, variable_name)`](@ref): retrieves the value from data[variable_name] regardless of type, not indexed by row, year or hour.
