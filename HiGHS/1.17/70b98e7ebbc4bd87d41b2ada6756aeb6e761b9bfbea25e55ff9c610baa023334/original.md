```
Highs_getColsByMask(highs, mask, num_col, costs, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

Get data associated with multiple columns given by a mask.

This function is identical to [`Highs_getColsByRange`](@ref), except for how the columns are specified.

### Parameters

  * `mask`: An array of length [num_col] containing a `1` to get the column and `0` otherwise.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
