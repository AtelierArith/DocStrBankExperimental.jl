```
Highs_changeColIntegrality(highs, col, integrality)
```

Change the integrality of a column.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col`: The column index to change.
  * `integrality`: The new integrality of the column in the form of a `kHighsVarType` constant.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
