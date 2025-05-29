```
summarize_table(::Val{:nominal_load})
```

| column_name | data_type | unit        | required | description                                        |
|:----------- |:--------- |:----------- |:-------- |:-------------------------------------------------- |
| `bus_idx`   | Int64     | E4ST.NA     | true     | The bus index of the load element                  |
| `plnom0`    | Float64   | E4ST.MWLoad | true     | The nominal load power of the load element         |
| `load_type` | String    | E4ST.NA     | false    | The type of load represented by this load element. |
