```
Highs_addCols(highs, num_new_col, costs, lower, upper, num_new_nz, starts, index, value)
```

Add multiple columns (variables) to the model.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_new_col`: The number of new columns to add.
  * `costs`: An array of size [num_new_col] with objective coefficients.
  * `lower`: An array of size [num_new_col] with lower bounds.
  * `upper`: An array of size [num_new_col] with upper bounds.
  * `num_new_nz`: The number of new nonzeros in the constraint matrix.
  * `starts`: The constraint coefficients are given as a matrix in compressed sparse column form by the arrays `starts`, `index`, and `value`. `starts` is an array of size [num_new_cols] with the start index of each row in indices and values.
  * `index`: An array of size [num_new_nz] with row indices.
  * `value`: An array of size [num_new_nz] with row values.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
