```
Highs_getSolution(highs, col_value, col_dual, row_value, row_dual)
```

Get the primal and dual solution from an optimized model.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col_value`: An array of length [num_col], to be filled with primal column values.
  * `col_dual`: An array of length [num_col], to be filled with dual column values.
  * `row_value`: An array of length [num_row], to be filled with primal row values.
  * `row_dual`: An array of length [num_row], to be filled with dual row values.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
