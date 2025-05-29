```
summarize_table(::Val{:nominal_load})
```

| column_name | data_type | unit        | required | description         |
|:----------- |:--------- |:----------- |:-------- |:------------------- |
| `bus_idx`   | Int64     | E4ST.NA     | true     | 負荷要素のバスインデックス       |
| `plnom0`    | Float64   | E4ST.MWLoad | true     | 負荷要素の名目負荷電力         |
| `load_type` | String    | E4ST.NA     | false    | この負荷要素によって表される負荷の種類 |
