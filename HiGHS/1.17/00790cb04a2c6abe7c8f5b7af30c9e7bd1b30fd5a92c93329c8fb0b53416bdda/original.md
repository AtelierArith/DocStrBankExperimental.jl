```
Highs_getColName(highs, col, name)
```

Get the name of a column.

### Parameters

  * `col`: The index of the column to query.
  * `name`: A pointer in which to store the name of the column. This must have length `kHighsMaximumStringLength`.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
