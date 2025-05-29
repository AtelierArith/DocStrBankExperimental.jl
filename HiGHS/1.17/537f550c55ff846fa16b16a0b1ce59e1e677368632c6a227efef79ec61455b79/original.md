```
Highs_getRowName(highs, row, name)
```

Get the name of a row.

### Parameters

  * `row`: The index of the row to query.
  * `name`: A pointer in which to store the name of the row. This must have length `kHighsMaximumStringLength`.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
