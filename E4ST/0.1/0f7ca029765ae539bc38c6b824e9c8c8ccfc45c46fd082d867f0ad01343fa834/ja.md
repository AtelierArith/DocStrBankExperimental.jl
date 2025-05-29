```
summarize_table(::Val{:interface_limit})
```

| column_name        | data_type | unit                   | required | description                                                                              |
|:------------------ |:--------- |:---------------------- |:-------- |:---------------------------------------------------------------------------------------- |
| `name`             | String    | E4ST.NA                | false    | インターフェース制限の名前、使用されていません                                                                  |
| `description`      | String    | E4ST.NA                | false    | インターフェース制限の説明、使用されていません。                                                                 |
| `f_filter`         | String    | E4ST.NA                | true     | 電力が流れる地域を指定するバステーブルのフィルター **f** から。 例： `nation=>narnia` または `state=>[angard, stormness]` |
| `t_filter`         | String    | E4ST.NA                | true     | 電力が流れる地域を指定するバステーブルのフィルター **t** へ。                                                       |
| `pflow_max`        | Float64   | E4ST.MWFlow            | false    | `f` から `t` への最大許容電力フロー。 ±Inf のままにすると、制約はありません。                                           |
| `pflow_min`        | Float64   | E4ST.MWFlow            | false    | `f` から `t` への最小許容電力フロー。 正または負の値にできます。 ±Inf のままにすると、制約はありません。                             |
| `eflow_yearly_max` | Float64   | E4ST.MWhFlow           | false    | `f` から `t` への年間最大許容エネルギー。 ±Inf のままにすると、制約はありません。                                         |
| `eflow_yearly_min` | Float64   | E4ST.MWhFlow           | false    | `f` から `t` への年間最小許容エネルギー。 正または負の値にできます。 ±Inf のままにすると、制約はありません。                           |
| `price`            | Float64   | E4ST.DollarsPerMWhFlow | false    | `f` から `t` へのネットフローの価格。                                                                  |
| `include_dc`       | Bool      | E4ST.NA                | false    | このインターフェース制限にDCラインを含めるかどうか。 提供されていない場合、DCラインは含まれていないと仮定されます。                             |
