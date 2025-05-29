```
Highs_getBasisInverseCol(highs, col, col_vector, col_num_nz, col_index)
```

Get a column of the inverse basis matrix $B^{-1}$.

See [`Highs_getBasicVariables`](@ref) for a description of the $B$ matrix.

The arrays `col_vector` and `col_index` must have an allocated length of [num_row]. However, check `col_num_nz` to see how many non-zero elements are actually stored.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col`: The index of the column to compute.
  * `col_vector`: An array of length [num_row] in which to store the values of the non-zero elements.
  * `col_num_nz`: The number of non-zeros in the column.
  * `col_index`: An array of length [num_row] in which to store the indices of the non-zero elements.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
