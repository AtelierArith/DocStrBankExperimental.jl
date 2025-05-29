```
summarize_table(::Val{:branch})
```

| column_name | data_type | unit        | required | description                                                            |
|:----------- |:--------- |:----------- |:-------- |:---------------------------------------------------------------------- |
| `f_bus_idx` | Int64     | E4ST.NA     | true     | The index of the `bus` table that the branch originates **f**rom       |
| `t_bus_idx` | Int64     | E4ST.NA     | true     | The index of the `bus` table that the branch goes **t**o               |
| `status`    | Bool      | E4ST.NA     | false    | Whether or not the branch is in service                                |
| `x`         | Float64   | E4ST.PU     | true     | Per-unit reactance of the line (resistance assumed to be 0 for DC-OPF) |
| `pflow_max` | Float64   | E4ST.MWFlow | true     | Maximum power flowing through the branch                               |
