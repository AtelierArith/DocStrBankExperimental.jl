```
summarize_table(::Val{:dc_line})
```

| column_name | data_type | unit        | required | description                                                    |
|:----------- |:--------- |:----------- |:-------- |:-------------------------------------------------------------- |
| `f_bus_idx` | Int64     | E4ST.NA     | true     | The index of the `bus` table that the line originates **f**rom |
| `t_bus_idx` | Int64     | E4ST.NA     | true     | The index of the `bus` table that the line goes **t**o         |
| `status`    | Bool      | E4ST.NA     | false    | Whether or not the dc line is in service                       |
| `pflow_max` | Float64   | E4ST.MWFlow | true     | Maximum power flowing through the dc line                      |
