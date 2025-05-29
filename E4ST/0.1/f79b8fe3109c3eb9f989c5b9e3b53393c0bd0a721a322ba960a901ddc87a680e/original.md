```
summarize_table(::Val{:adjust_yearly})
```

| column_name     | data_type      | unit       | required | description                                                                                                                                                                                                        |
|:--------------- |:-------------- |:---------- |:-------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `table_name`    | AbstractString | E4ST.NA    | true     | The name of the table to adjust.  Leave blank if this adjustment is intended for a variable in `data`                                                                                                              |
| `variable_name` | AbstractString | E4ST.NA    | true     | The name of the variable/column to adjust                                                                                                                                                                          |
| `operation`     | E4ST.Operation | E4ST.NA    | true     | The operation to perform.  Could be add, scale, or set.                                                                                                                                                            |
| `filter_`       | String         | E4ST.NA    | true     | There can be multiple filter conditions - `filter1`, `filter2`, etc.  It denotes a comparison used for selecting the table rows to apply the adjustment to.  See `parse_comparison` for examples                   |
| `year_col`      | String         | E4ST.NA    | false    | Optional, the column for which the adjustment applies.  For example, use `year_on` to set a cost for the lifetime of a generator.  Leave blank (default) for to apply the adjustment by the simulation year value. |
| `status`        | Bool           | E4ST.NA    | false    | Whether or not to use this adjustment                                                                                                                                                                              |
| `y_`            | Float64        | E4ST.Ratio | true     | Value to adjust by for each year.  Include a column for each year in the hours table.  I.e. `:y2020`, `:y2030`, etc                                                                                                |
