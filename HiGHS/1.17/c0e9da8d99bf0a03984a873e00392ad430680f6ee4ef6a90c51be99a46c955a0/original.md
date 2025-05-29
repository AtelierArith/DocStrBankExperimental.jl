```
Highs_getColIntegrality(highs, col, integrality)
```

Get the integrality of a column.

### Parameters

  * `col`: The index of the column to query.
  * `integrality`: An integer in which the integrality of the column should be placed. The integer is one of the `kHighsVarTypeXXX` constants.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
