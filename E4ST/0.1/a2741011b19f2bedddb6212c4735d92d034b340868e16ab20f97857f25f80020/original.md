```
summarize_table(::Val{:reserve_flow_limits})
```

| column_name         | data_type | unit        | required | description                                                 |
|:------------------- |:--------- |:----------- |:-------- |:----------------------------------------------------------- |
| `f_subarea`         | Any       | E4ST.NA     | true     | The subarea the reserve power flow originates **f**rom      |
| `t_subarea`         | Any       | E4ST.NA     | true     | The subarea the reserve power flow goes **t**o              |
| `pflow_forward_max` | Float64   | E4ST.MWFlow | true     | Maximum reserve power going from `f_subarea` to `t_subarea` |
| `pflow_reverse_max` | Float64   | E4ST.MWFlow | true     | Maximum reserve power going from `t_subarea` to `f_subarea` |
