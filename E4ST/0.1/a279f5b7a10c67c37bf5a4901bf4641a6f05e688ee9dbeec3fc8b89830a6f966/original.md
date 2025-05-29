```
summarize_table(::Val{:reserve_requirements})
```

| column_name | data_type | unit       | required | description                                                                                                                                  |
|:----------- |:--------- |:---------- |:-------- |:-------------------------------------------------------------------------------------------------------------------------------------------- |
| `subarea`   | Any       | E4ST.NA    | true     | The subarea that the requirement is specified over                                                                                           |
| `y_`        | Float64   | E4ST.Ratio | true     | The percent requirement of reserve capacity over the load.  Include a column for each year in the hours table.  I.e. `:y2020`, `:y2030`, etc |
