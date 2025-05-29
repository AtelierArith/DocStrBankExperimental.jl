```
AdjustHourly(;file, name)
```

Adjusts tables and parameters by hour.  Stores the table stored in `file` into `data[name]`.

| column_name     | data_type      | unit       | required | description                                                                                                                                                                                      |
|:--------------- |:-------------- |:---------- |:-------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `table_name`    | AbstractString | E4ST.NA    | true     | The name of the table to adjust.  Leave blank if this adjustment is intended for a variable in `data`                                                                                            |
| `variable_name` | AbstractString | E4ST.NA    | true     | The name of the variable/column to adjust                                                                                                                                                        |
| `operation`     | E4ST.Operation | E4ST.NA    | true     | The operation to perform.  Could be add, scale, or set.                                                                                                                                          |
| `filter_`       | String         | E4ST.NA    | true     | There can be multiple filter conditions - `filter1`, `filter2`, etc.  It denotes a comparison used for selecting the table rows to apply the adjustment to.  See `parse_comparison` for examples |
| `year`          | String         | E4ST.Year  | true     | The year to adjust, expressed as a year string prepended with a "y".  I.e. "y2022".  Leave blank to adjust all years                                                                             |
| `status`        | Bool           | E4ST.NA    | false    | Whether or not to use this adjustment                                                                                                                                                            |
| `h_`            | Float64        | E4ST.Ratio | true     | Value to adjust by for each hour.  Include a column for each hour in the hours table.  I.e. `:h1`, `:h2`, ... `:hn`                                                                              |
