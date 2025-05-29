```
summarize_table(::Val{:branch})
```

| column_name | data_type | unit        | required | description                         |
|:----------- |:--------- |:----------- |:-------- |:----------------------------------- |
| `f_bus_idx` | Int64     | E4ST.NA     | true     | ブランチが**f**rom始まる`bus`テーブルのインデックス    |
| `t_bus_idx` | Int64     | E4ST.NA     | true     | ブランチが**t**o向かう`bus`テーブルのインデックス      |
| `status`    | Bool      | E4ST.NA     | false    | ブランチが稼働中かどうか                        |
| `x`         | Float64   | E4ST.PU     | true     | ラインのパーユニットリアクタンス（DC-OPFの場合、抵抗は0と仮定） |
| `pflow_max` | Float64   | E4ST.MWFlow | true     | ブランチを通る最大電力                         |
