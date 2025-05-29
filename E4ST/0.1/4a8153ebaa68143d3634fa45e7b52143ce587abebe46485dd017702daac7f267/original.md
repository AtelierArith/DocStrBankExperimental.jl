```
AdjustString(;file, name)
```

Adjusts tables and parameters by setting a string.  Stores the table stored in `file` into `data[name]`.

| column_name     | data_type      | unit    | required | description                                                                                                                                                                                      |
|:--------------- |:-------------- |:------- |:-------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `table_name`    | AbstractString | E4ST.NA | true     | The name of the table to adjust.  Leave blank if this adjustment is intended for a variable in `data`                                                                                            |
| `variable_name` | AbstractString | E4ST.NA | true     | The name of the variable/column to adjust                                                                                                                                                        |
| `filter_`       | String         | E4ST.NA | true     | There can be multiple filter conditions - `filter1`, `filter2`, etc.  It denotes a comparison used for selecting the table rows to apply the adjustment to.  See `parse_comparison` for examples |
| `status`        | Bool           | E4ST.NA | false    | Whether or not to use this adjustment                                                                                                                                                            |
| `value`         | String         | E4ST.NA | true     | Value to set to.                                                                                                                                                                                 |
