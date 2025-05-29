```
Highs_getBasisInverseRow(highs, row, row_vector, row_num_nz, row_index)
```

Get a row of the inverse basis matrix $B^{-1}$.

See [`Highs_getBasicVariables`](@ref) for a description of the $B$ matrix.

The arrays `row_vector` and `row_index` must have an allocated length of [num_row]. However, check `row_num_nz` to see how many non-zero elements are actually stored.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `row`: The index of the row to compute.
  * `row_vector`: An array of length [num_row] in which to store the values of the non-zero elements.
  * `row_num_nz`: The number of non-zeros in the row.
  * `row_index`: An array of length [num_row] in which to store the indices of the non-zero elements.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
