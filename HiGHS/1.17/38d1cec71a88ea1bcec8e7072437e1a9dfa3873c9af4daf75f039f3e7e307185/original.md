```
Highs_changeColsIntegralityByRange(highs, from_col, to_col, integrality)
```

Change the integrality of multiple adjacent columns.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `from_col`: The index of the first column whose integrality changes.
  * `to_col`: The index of the last column whose integrality changes.
  * `integrality`: An array of length [to_col - from_col + 1] with the new integralities of the columns in the form of `kHighsVarType` constants.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
