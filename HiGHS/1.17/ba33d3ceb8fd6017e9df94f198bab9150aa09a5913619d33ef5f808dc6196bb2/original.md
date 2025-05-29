```
Highs_getRowsByMask(highs, mask, num_row, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

Get data associated with multiple rows given by a mask.

This function is identical to [`Highs_getRowsByRange`](@ref), except for how the rows are specified.

### Parameters

  * `mask`: An array of length [num_row] containing a `1` to get the row and `0` otherwise.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
