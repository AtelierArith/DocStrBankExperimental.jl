```
Highs_addCol(highs, cost, lower, upper, num_new_nz, index, value)
```

Add a new column (variable) to the model.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `cost`: The objective coefficient of the column.
  * `lower`: The lower bound of the column.
  * `upper`: The upper bound of the column.
  * `num_new_nz`: The number of non-zeros in the column.
  * `index`: An array of size [num_new_nz] with the row indices.
  * `value`: An array of size [num_new_nz] with row values.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
