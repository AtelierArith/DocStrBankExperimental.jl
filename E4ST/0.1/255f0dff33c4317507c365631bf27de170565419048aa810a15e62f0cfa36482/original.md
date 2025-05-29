```
summarize_table(::Val{:hours})
```

| column_name | data_type | unit       | required | description                                                                                        |
|:----------- |:--------- |:---------- |:-------- |:-------------------------------------------------------------------------------------------------- |
| `hours`     | Float64   | E4ST.Hours | true     | The number of hours spent in each representative hour over the course of a year (must sum to 8760) |
