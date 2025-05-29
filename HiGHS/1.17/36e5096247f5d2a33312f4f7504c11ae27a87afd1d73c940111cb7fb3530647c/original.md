```
Highs_changeColsBoundsByRange(highs, from_col, to_col, lower, upper)
```

Change the variable bounds of multiple adjacent columns.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `from_col`: The index of the first column whose bound changes.
  * `to_col`: The index of the last column whose bound changes.
  * `lower`: An array of length [to_col - from_col + 1] with the new lower bounds.
  * `upper`: An array of length [to_col - from_col + 1] with the new upper bounds.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
