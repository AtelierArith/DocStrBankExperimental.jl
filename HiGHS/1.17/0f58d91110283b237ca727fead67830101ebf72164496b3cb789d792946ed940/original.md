```
Highs_setSolution(highs, col_value, row_value, col_dual, row_dual)
```

Set a solution by passing the column and row primal and dual solution values.

For any values that are unavailable, pass NULL.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col_value`: An array of length [num_col] with the column solution values.
  * `row_value`: An array of length [num_row] with the row solution values.
  * `col_dual`: An array of length [num_col] with the column dual values.
  * `row_dual`: An array of length [num_row] with the row dual values.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
