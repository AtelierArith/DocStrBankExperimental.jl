```
summarize_table(::Val{:load_shape})
```

| column_name | data_type | unit       | required | description                                                                                                      |
|:----------- |:--------- |:---------- |:-------- |:---------------------------------------------------------------------------------------------------------------- |
| `area`      | String    | E4ST.NA    | true     | The area with which to filter by. I.e. "state". Leave blank to not filter by area.                               |
| `subarea`   | String    | E4ST.NA    | true     | The subarea to include in the filter.  I.e. "maryland".  Leave blank to not filter by area.                      |
| `load_type` | String    | E4ST.NA    | false    | The type of load represented for this load shape.  Leave blank to not filter by type.                            |
| `year`      | String    | E4ST.Year  | false    | The year to apply the load profile to, expressed as a year string prepended with a "y".  I.e. "y2022"            |
| `status`    | Bool      | E4ST.NA    | false    | Whether or not to use this shape adjustment                                                                      |
| `h_`        | Float64   | E4ST.Ratio | true     | Load scaling factor of hour 1.  Include a column for each hour in the hours table.  I.e. `:h1`, `:h2`, ... `:hn` |
