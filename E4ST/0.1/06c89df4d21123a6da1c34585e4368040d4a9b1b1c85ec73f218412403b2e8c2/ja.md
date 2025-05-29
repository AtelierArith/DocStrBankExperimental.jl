```
AdjustByAge(;file, name)
```

年ごとにテーブルとパラメータを調整します。 `file` に保存されているテーブルを `data[name]` に格納します。

| column_name     | data_type      | unit          | required | description                                                                                                                                                                            |
|:--------------- |:-------------- |:------------- |:-------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `table_name`    | AbstractString | E4ST.NA       | true     | 調整するテーブルの名前。 この調整が `data` の変数に対して意図されている場合は空白のままにします。                                                                                                                                  |
| `variable_name` | AbstractString | E4ST.NA       | true     | 調整する変数/列の名前                                                                                                                                                                            |
| `operation`     | E4ST.Operation | E4ST.NA       | true     | 実行する操作。 加算、スケール、または設定が可能です。                                                                                                                                                            |
| `filter_`       | String         | E4ST.NA       | true     | 複数のフィルター条件が存在する場合があります - `filter1`、`filter2` など。 調整を適用するテーブル行を選択するために使用される比較を示します。 例については `parse_comparison` を参照してください。                                                                |
| `status`        | Bool           | E4ST.NA       | false    | この調整を使用するかどうか                                                                                                                                                                          |
| `age_type`      | String         | E4ST.NA       | true     | 指定された年齢のタイプ。 `exact`、`after`、または `trigger` のいずれかです。 `exact` の場合、調整は年齢が `[age, age+1)` の間にあるときのみ適用されます。 `trigger` の場合、調整は年齢が超えた最初のシミュレーション年に適用されます。 `after` の場合、調整は [age, Inf) に適用されます。 |
| `age`           | Float64        | E4ST.NumYears | true     | この調整を適用する年齢。 `age_type` に応じて適用されます。                                                                                                                                                    |
| `value`         | Float64        | E4ST.NA       | true     | 調整する値。                                                                                                                                                                                 |
