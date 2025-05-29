```
summarize_table(::Val{:bus})
```

| column_name  | data_type | unit    | required | description                      |
|:------------ |:--------- |:------- |:-------- |:-------------------------------- |
| `ref_bus`    | Bool      | E4ST.NA | true     | バスが基準バスであるかどうか。各島には1つの基準バスが必要です。 |
| `reg_factor` | Float64   | E4ST.NA | true     | コストサービス規制市場に dispatch される発電の割合   |
