```
AggregationTemplate(;file, name) <: Modification
```

This is a mod that outputs aggregated results, given a `file` representing the template of the things to be aggregated.  `name` is simply the name of the modification, and will be used as the root for the filename that the aggregated information is saved to.

The `file` should represent a csv table with the following columns:

  * `table_name` - the name of the table being aggregated.  i.e. `gen`, `bus`, etc.
  * `result_name` - the name of the column in the table being aggregated.  Note that the column must have a Unit accessible via [`get_table_col_unit`](@ref).
  * `filter_` - the filtering conditions for the rows of the table. I.e. `filter1`.  See [`parse_comparisons`](@ref) for information on what types of filters could be provided.
  * `filter_years` - the filtering conditions for the years to be aggregated.  See [`parse_year_idxs`](@ref) for information on the year filters.
  * `filter_hours` - the filtering conditions for the hours to be aggregated.  See [`parse_hour_idxs`](@ref) for information on the hour filters.

Note that, for the `filter_` or `filter_hours` columns, if a column name of the data table (or hours table) is given, new rows will be created for each unique value of that column.  I.e. if a value of `gentype` is given, there will be made a new row for `gentype=>coal`, `gentype=>ng`, etc.
