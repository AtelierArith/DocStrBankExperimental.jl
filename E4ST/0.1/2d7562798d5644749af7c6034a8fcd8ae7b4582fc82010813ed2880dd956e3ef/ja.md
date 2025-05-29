```
summarize_table(::Val{:adjust_string})
```

| column_name     | data_type      | unit    | required | description                                                                                                       |
|:--------------- |:-------------- |:------- |:-------- |:----------------------------------------------------------------------------------------------------------------- |
| `table_name`    | AbstractString | E4ST.NA | true     | 調整するテーブルの名前。`data`内の変数に対する調整である場合は空白のままにしてください。                                                                   |
| `variable_name` | AbstractString | E4ST.NA | true     | 調整する変数/列の名前                                                                                                       |
| `filter_`       | String         | E4ST.NA | true     | 複数のフィルター条件を指定できます - `filter1`、`filter2`など。これは、調整を適用するテーブル行を選択するために使用される比較を示します。例については`parse_comparison`を参照してください。 |
| `status`        | Bool           | E4ST.NA | false    | この調整を使用するかどうか                                                                                                     |
| `value`         | String         | E4ST.NA | true     | 設定する値。                                                                                                            |
