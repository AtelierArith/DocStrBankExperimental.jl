```
summarize_table(::Val{:adjust_yearly})
```

| column_name     | data_type      | unit       | required | description                                                                                              |
|:--------------- |:-------------- |:---------- |:-------- |:-------------------------------------------------------------------------------------------------------- |
| `table_name`    | AbstractString | E4ST.NA    | true     | 調整するテーブルの名前。`data`内の変数に対する調整である場合は空白のままにしてください。                                                          |
| `variable_name` | AbstractString | E4ST.NA    | true     | 調整する変数/列の名前                                                                                              |
| `operation`     | E4ST.Operation | E4ST.NA    | true     | 実行する操作。加算、スケール、または設定が可能です。                                                                               |
| `filter_`       | String         | E4ST.NA    | true     | 複数のフィルター条件を指定できます - `filter1`、`filter2`など。調整を適用するテーブル行を選択するための比較を示します。例については`parse_comparison`を参照してください。 |
| `year_col`      | String         | E4ST.NA    | false    | オプション、調整が適用される列。例えば、発電機の寿命に対するコストを設定するために`year_on`を使用します。シミュレーション年の値で調整を適用するためには空白（デフォルト）にしてください。        |
| `status`        | Bool           | E4ST.NA    | false    | この調整を使用するかどうか                                                                                            |
| `y_`            | Float64        | E4ST.Ratio | true     | 各年ごとに調整する値。時間テーブルに各年の列を含めてください。すなわち、`:y2020`、`:y2030`など。                                                 |
