```
summarize_table(::Val{:ccus_paths})
```

| column_name        | data_type | unit                    | required | description                                                                                 |
|:------------------ |:--------- |:----------------------- |:-------- |:------------------------------------------------------------------------------------------- |
| `producing_region` | String    | E4ST.NA                 | true     | The name of the producing region (type of regions specified by groupby kwarg of CCUS mod    |
| `storing_region`   | String    | E4ST.NA                 | true     | The name of the sequestering region (type of regions specified by groupby kwarg of CCUS mod |
| `step_id`          | Int64     | E4ST.NA                 | true     | The number of this particular market step                                                   |
| `ccus_type`        | String    | E4ST.NA                 | true     | The type of storage.  Can be "eor" or "saline"                                              |
| `step_quantity`    | Float64   | E4ST.ShortTonsPerYear   | true     | The annual quantity of CO2 that can be stored in the step                                   |
| `price_trans`      | Float64   | E4ST.DollarsPerShortTon | true     | The cost of transporting a short ton of CO2 for this producer-storing_region pair           |
| `price_store`      | Float64   | E4ST.DollarsPerShortTon | true     | The cost to store a short ton of CO2 in this storage step                                   |
