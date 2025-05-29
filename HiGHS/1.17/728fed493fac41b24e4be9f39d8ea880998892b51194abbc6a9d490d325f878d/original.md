```
Highs_crossover(highs, num_col, num_row, col_value, col_dual, row_dual)
```

Set a primal (and possibly dual) solution as a starting point, then run crossover to compute a basic feasible solution.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_col`: The number of variables.
  * `num_row`: The number of rows.
  * `col_value`: An array of length [num_col] with optimal primal solution for each column.
  * `col_dual`: An array of length [num_col] with optimal dual solution for each column. May be `NULL`, in which case no dual solution is passed.
  * `row_dual`: An array of length [num_row] with optimal dual solution for each row. . May be `NULL`, in which case no dual solution is passed.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
