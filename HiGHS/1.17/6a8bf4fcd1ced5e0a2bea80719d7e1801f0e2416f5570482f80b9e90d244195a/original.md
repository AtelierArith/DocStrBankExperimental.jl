```
Highs_setBasis(highs, col_status, row_status)
```

Set a basic feasible solution by passing the column and row basis statuses to the model.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col_status`: an array of length [num_col] with the column basis status in the form of `kHighsBasisStatus` constants
  * `row_status`: an array of length [num_row] with the row basis status in the form of `kHighsBasisStatus` constants

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
