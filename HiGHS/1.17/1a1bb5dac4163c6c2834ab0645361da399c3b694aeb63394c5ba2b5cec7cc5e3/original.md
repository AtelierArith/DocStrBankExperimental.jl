```
Highs_getBasis(highs, col_status, row_status)
```

Given a linear program with a basic feasible solution, get the column and row basis statuses.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col_status`: An array of length [num_col], to be filled with the column basis statuses in the form of a `kHighsBasisStatus` constant.
  * `row_status`: An array of length [num_row], to be filled with the row basis statuses in the form of a `kHighsBasisStatus` constant.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
