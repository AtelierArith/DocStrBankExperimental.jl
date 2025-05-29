```
add_to_results_formula!(data, table_name::Symbol, result_name::Symbol, formula)
```

既存の結果の数式に項を追加します。より複雑な式も可能です。

  * 派生数式（例えば `"vom_cost + fom_cost"`）の場合、数式に追加するために任意の式を提供できます。例えば `"-my_result_name / 2"` のように。
  * 主数式（例えば `"SumHourly(col1, col2)"`）の場合、追加の列を `"col3, col4"` のように提供できます。
