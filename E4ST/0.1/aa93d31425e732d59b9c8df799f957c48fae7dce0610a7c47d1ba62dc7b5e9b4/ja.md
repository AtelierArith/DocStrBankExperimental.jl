```
summarize_table(::Val{:adjust_hourly})
```

| column_name     | data_type      | unit       | required | description                                                                                                         |
|:--------------- |:-------------- |:---------- |:-------- |:------------------------------------------------------------------------------------------------------------------- |
| `table_name`    | AbstractString | E4ST.NA    | true     | 調整するテーブルの名前。`data`内の変数に対する調整である場合は空白のままにしてください。                                                                     |
| `variable_name` | AbstractString | E4ST.NA    | true     | 調整する変数/列の名前                                                                                                         |
| `operation`     | E4ST.Operation | E4ST.NA    | true     | 実行する操作。加算、スケール、または設定が可能です。                                                                                          |
| `filter_`       | String         | E4ST.NA    | true     | 複数のフィルター条件が存在する可能性があります - `filter1`、`filter2`など。調整を適用するテーブル行を選択するために使用される比較を示します。例については`parse_comparison`を参照してください。 |
| `year`          | String         | E4ST.Year  | true     | 調整する年を、"y"を前置した年文字列として表現します。すなわち、"y2022"。すべての年を調整するには空白のままにしてください。                                                  |
| `status`        | Bool           | E4ST.NA    | false    | この調整を使用するかどうか                                                                                                       |
| `h_`            | Float64        | E4ST.Ratio | true     | 各時間ごとに調整する値。時間テーブルの各時間に対して列を含めてください。すなわち、`:h1`、`:h2`、... `:hn`                                                      |
