```
summarize_table(::Val{:reserve_flow_limits})
```

| column_name         | data_type | unit        | required | description                      |
|:------------------- |:--------- |:----------- |:-------- |:-------------------------------- |
| `f_subarea`         | Any       | E4ST.NA     | true     | 予備電力フローが**f**から発生するサブエリア         |
| `t_subarea`         | Any       | E4ST.NA     | true     | 予備電力フローが**t**に向かうサブエリア           |
| `pflow_forward_max` | Float64   | E4ST.MWFlow | true     | `f_subarea`から`t_subarea`への最大予備電力 |
| `pflow_reverse_max` | Float64   | E4ST.MWFlow | true     | `t_subarea`から`f_subarea`への最大予備電力 |
