```
add_to_results_formula!(data, table_name::Symbol, result_name::Symbol, formula)
```

Adds a term to an existing results formula.  Can be more complex expressions.

  * if it is a derived formula (like `"vom_cost + fom_cost"`), then you can supply any expression to get added to the formula, like `"-my_result_name / 2"`
  * if it is a primary formula (like `"SumHourly(col1, col2)"`), then you can provide additional columns like `"col3, col4"`.
