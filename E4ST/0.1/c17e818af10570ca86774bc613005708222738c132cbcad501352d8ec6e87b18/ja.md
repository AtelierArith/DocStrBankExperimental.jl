```
summarize_table(::Val{:dc_line})
```

| column_name | data_type | unit        | required | description                    |
|:----------- |:--------- |:----------- |:-------- |:------------------------------ |
| `f_bus_idx` | Int64     | E4ST.NA     | true     | ラインが**f**から始まる`bus`テーブルのインデックス |
| `t_bus_idx` | Int64     | E4ST.NA     | true     | ラインが**t**に向かう`bus`テーブルのインデックス  |
| `status`    | Bool      | E4ST.NA     | false    | dcラインが稼働中かどうか                  |
| `pflow_max` | Float64   | E4ST.MWFlow | true     | dcラインを流れる最大電力                  |
