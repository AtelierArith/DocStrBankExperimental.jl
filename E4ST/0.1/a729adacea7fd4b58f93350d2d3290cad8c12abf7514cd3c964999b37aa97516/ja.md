```
summarize_table(::Val{:annual_cf_lim})
```

| column_name     | data_type      | unit                            | required | description                                                                                                      |
|:--------------- |:-------------- |:------------------------------- |:-------- |:---------------------------------------------------------------------------------------------------------------- |
| `genfuel`       | AbstractString | E4ST.NA                         | false    | 発電機が使用する燃料の種類。genfuelでフィルタリングしない場合は空白のままにしてください。                                                                 |
| `gentype`       | String         | E4ST.NA                         | false    | 発電機が使用する発電技術の種類。gentypeでフィルタリングしない場合は空白のままにしてください。                                                               |
| `area`          | AbstractString | E4ST.NA                         | false    | フィルタリングする地域。すなわち「州」。areaでフィルタリングしない場合は空白のままにしてください。                                                              |
| `subarea`       | AbstractString | E4ST.NA                         | false    | フィルタに含めるサブエリア。すなわち「メリーランド」。areaでフィルタリングしない場合は空白のままにしてください。                                                       |
| `filter_`       | String         | E4ST.NA                         | false    | 複数のフィルタ条件を指定できます - `filter1`、`filter2`など。これは、調整を適用するテーブル行を選択するために使用される比較を示します。例については`parse_comparison`を参照してください。 |
| `status`        | Bool           | E4ST.NA                         | false    | この制限を使用するかどうか                                                                                                    |
| `annual_cf_min` | Float64        | E4ST.MWhGeneratedPerMWhCapacity | false    | 最小年間容量係数 ∈ (0,1]。これらの範囲外の場合は設定されません。矛盾する可用性要因があるとモデルが実行不可能になるため、非常に注意してください。                                     |
| `annual_cf_max` | Float64        | E4ST.MWhGeneratedPerMWhCapacity | false    | 最大年間容量係数 ∈ [0,1)。これらの範囲外の場合は設定されません。                                                                             |
