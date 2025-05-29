```
Highs_addRow(highs, lower, upper, num_new_nz, index, value)
```

Add a new row (a linear constraint) to the model.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `lower`: The lower bound of the row.
  * `upper`: The upper bound of the row.
  * `num_new_nz`: The number of non-zeros in the row
  * `index`: An array of size [num_new_nz] with column indices.
  * `value`: An array of size [num_new_nz] with column values.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
