```
summarize_table(::Val{:ccus_paths})
```

| column_name        | data_type | unit                    | required | description                              |
|:------------------ |:--------- |:----------------------- |:-------- |:---------------------------------------- |
| `producing_region` | String    | E4ST.NA                 | true     | 生産地域の名前（CCUSモジュールのgroupby引数で指定された地域のタイプ） |
| `storing_region`   | String    | E4ST.NA                 | true     | 貯蔵地域の名前（CCUSモジュールのgroupby引数で指定された地域のタイプ） |
| `step_id`          | Int64     | E4ST.NA                 | true     | この特定の市場ステップの番号                           |
| `ccus_type`        | String    | E4ST.NA                 | true     | 貯蔵のタイプ。 "eor" または "saline" である可能性があります。  |
| `step_quantity`    | Float64   | E4ST.ShortTonsPerYear   | true     | このステップで貯蔵できるCO2の年間量                      |
| `price_trans`      | Float64   | E4ST.DollarsPerShortTon | true     | この生産者-貯蔵地域ペアのための短トンのCO2を輸送するコスト          |
| `price_store`      | Float64   | E4ST.DollarsPerShortTon | true     | この貯蔵ステップで短トンのCO2を貯蔵するコスト                 |
