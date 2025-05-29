```
Highs_addRows(highs, num_new_row, lower, upper, num_new_nz, starts, index, value)
```

Add multiple rows (linear constraints) to the model.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_new_row`: The number of new rows to add
  * `lower`: An array of size [num_new_row] with the lower bounds of the rows.
  * `upper`: An array of size [num_new_row] with the upper bounds of the rows.
  * `num_new_nz`: The number of non-zeros in the rows.
  * `starts`: The constraint coefficients are given as a matrix in compressed sparse row form by the arrays `starts`, `index`, and `value`. `starts` is an array of size [num_new_rows] with the start index of each row in indices and values.
  * `index`: An array of size [num_new_nz] with column indices.
  * `value`: An array of size [num_new_nz] with column values.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
