```
get_table_num(data, table_name, col_name, row_idx, yr_idx, hr_idx) -> num::Float64
```

Retrieves a `Float64` from  `table[row_idx, col_idx][yr_idx, hr_idx]`.  This indexes into [`Container`](@ref)s as needed and will still work for `Float64` columns.

Related functions:

  * [`get_table_val(data, table_name, col_name, row_idx)`](@ref): retrieves the raw value from the table (without indexing by year/hour).
  * [`get_num(data, name, yr_idx, hr_idx)`](@ref): retrieves a `Float64` from `data`, indexing by year and hour.
