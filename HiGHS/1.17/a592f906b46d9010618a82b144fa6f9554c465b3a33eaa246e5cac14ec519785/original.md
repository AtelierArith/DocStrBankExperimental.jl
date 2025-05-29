```
Highs_changeColsCostByRange(highs, from_col, to_col, cost)
```

Change the cost coefficients of multiple adjacent columns.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `from_col`: The index of the first column whose cost changes.
  * `to_col`: The index of the last column whose cost changes.
  * `cost`: An array of length [to_col - from_col + 1] with the new objective coefficients.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
