```
Highs_getRowsBySet(highs, num_set_entries, set, num_row, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

Get data associated with multiple rows given by an array.

This function is identical to [`Highs_getRowsByRange`](@ref), except for how the rows are specified.

### Parameters

  * `num_set_indices`: The number of indices in `set`.
  * `set`: An array of size [num_set_entries] containing the row indices to get.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
