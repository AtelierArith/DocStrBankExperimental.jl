```
summarize_table(::Val{:results_formulas})
```

| column_name   | data_type         | unit    | required | description                                                                                                   |
|:------------- |:----------------- |:------- |:-------- |:------------------------------------------------------------------------------------------------------------- |
| `table_name`  | Symbol            | E4ST.NA | true     | The name of the table that the result is for.                                                                 |
| `result_name` | Symbol            | E4ST.NA | true     | The name of the result that the formula is for.                                                               |
| `formula`     | String            | E4ST.NA | true     | The string representing the formula for the table.  See [`add_results_formula!`](@ref) for more info on this. |
| `unit`        | Type{<:E4ST.Unit} | E4ST.NA | true     | The unit for the result.                                                                                      |
| `description` | String            | E4ST.NA | true     | A description of the result.                                                                                  |
