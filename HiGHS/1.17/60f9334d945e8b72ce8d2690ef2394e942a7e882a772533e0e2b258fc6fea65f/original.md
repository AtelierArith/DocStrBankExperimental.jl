```
Highs_getColsBySet(highs, num_set_entries, set, num_col, costs, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

Get data associated with multiple columns given by an array.

This function is identical to [`Highs_getColsByRange`](@ref), except for how the columns are specified.

### Parameters

  * `num_set_indices`: The number of indices in `set`.
  * `set`: An array of size [num_set_entries] with the column indices to get.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
