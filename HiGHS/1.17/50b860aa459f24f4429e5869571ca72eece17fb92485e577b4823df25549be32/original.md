```
Highs_changeCoeff(highs, row, col, value)
```

Change a coefficient in the constraint matrix.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `row`: The index of the row to change.
  * `col`: The index of the column to change.
  * `value`: The new constraint coefficient.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
