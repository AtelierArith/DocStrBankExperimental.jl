```
summarize_table(::Val{:bus})
```

| column_name  | data_type | unit    | required | description                                                                                         |
|:------------ |:--------- |:------- |:-------- |:--------------------------------------------------------------------------------------------------- |
| `ref_bus`    | Bool      | E4ST.NA | true     | Whether or not the bus is a reference bus.  There should be a single reference bus for each island. |
| `reg_factor` | Float64   | E4ST.NA | true     | The percentage of generation that dispatches to a cost-of-service regulated market                  |
