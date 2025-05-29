```
summarize_table(::Val{:results_formulas})
```

| column_name   | data_type         | unit    | required | description                                                       |
|:------------- |:----------------- |:------- |:-------- |:----------------------------------------------------------------- |
| `table_name`  | Symbol            | E4ST.NA | true     | 結果が対象とするテーブルの名前。                                                  |
| `result_name` | Symbol            | E4ST.NA | true     | フォーミュラが対象とする結果の名前。                                                |
| `formula`     | String            | E4ST.NA | true     | テーブルのフォーミュラを表す文字列。詳細については[`add_results_formula!`](@ref)を参照してください。 |
| `unit`        | Type{<:E4ST.Unit} | E4ST.NA | true     | 結果の単位。                                                            |
| `description` | String            | E4ST.NA | true     | 結果の説明。                                                            |
