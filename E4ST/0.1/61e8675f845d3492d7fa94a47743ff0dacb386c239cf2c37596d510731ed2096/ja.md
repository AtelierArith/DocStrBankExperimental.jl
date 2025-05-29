```
summarize_table(::Val{:fuel_price})
```

| column_name | data_type | unit                 | required | description                                                                                       |
|:----------- |:--------- |:-------------------- |:-------- |:------------------------------------------------------------------------------------------------- |
| `genfuel`   | String    | E4ST.NA              | true     | 価格が適用される燃料の種類。すなわち、`ng` または `coal`                                                                |
| `area`      | String    | E4ST.NA              | true     | 価格が適用される地域。すなわち、`nation`。グリッド全体の場合は空白のままにしてください。                                                  |
| `subarea`   | String    | E4ST.NA              | true     | 価格が適用されるサブエリア。すなわち、`narnia`。グリッド全体の場合は空白のままにしてください。                                               |
| `filter_`   | String    | E4ST.NA              | false    | すなわち、`filter1`、`filter2` など。価格が適用される他のフィルター条件については、アイデアのために [`parse_comparison`](@ref) を参照してください。 |
| `price`     | Float64   | E4ST.DollarsPerMMBtu | true     | 1 MMBtu の燃料の価格                                                                                    |
| `quantity`  | Float64   | E4ST.MMBtu           | true     | 各年においてその価格で利用可能な燃料の MMBtu 数。無制限の場合は `Inf` に設定してください。                                              |
