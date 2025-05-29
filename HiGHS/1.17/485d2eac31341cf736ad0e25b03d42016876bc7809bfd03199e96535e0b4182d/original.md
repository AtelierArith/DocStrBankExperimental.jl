```
Highs_getRowsByRange(highs, from_row, to_row, num_row, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

Get data associated with multiple adjacent rows from the model.

To query the constraint coefficients, this function should be called twice.

First, call this function with `matrix_start`, `matrix_index`, and `matrix_value` as `NULL`. This call will populate `num_nz` with the number of nonzero elements in the corresponding section of the constraint matrix.

Second, allocate new `matrix_index` and `matrix_value` arrays of length `num_nz` and call this function again to populate the new arrays with their contents.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `from_row`: The first row for which to query data for.
  * `to_row`: The last row (inclusive) for which to query data for.
  * `num_row`: An integer to be populated with the number of rows got from the model.
  * `lower`: An array of size [to_row - from_row + 1] for the row lower bounds.
  * `upper`: An array of size [to_row - from_row + 1] for the row upper bounds.
  * `num_nz`: An integer to be populated with the number of non-zero elements in the constraint matrix.
  * `matrix_start`: An array of size [to_row - from_row + 1] with the start indices of each row in `matrix_index` and `matrix_value`.
  * `matrix_index`: An array of size [num_nz] with the column indices of each element in the constraint matrix.
  * `matrix_value`: An array of size [num_nz] with the non-zero elements of the constraint matrix.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
