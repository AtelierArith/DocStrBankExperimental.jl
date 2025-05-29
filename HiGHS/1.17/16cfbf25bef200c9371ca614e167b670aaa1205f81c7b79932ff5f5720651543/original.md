```
Highs_postsolve(highs, col_value, col_dual, row_dual)
```

Postsolve a model using a primal (and possibly dual) solution.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col_value`: An array of length [num_col] with the column solution values.
  * `col_dual`: An array of length [num_col] with the column dual values, or a null pointer if not known.
  * `row_dual`: An array of length [num_row] with the row dual values, or a null pointer if not known.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
