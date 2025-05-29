```
Highs_getRowByName(highs, name, row)
```

Get the index of a row from its name.

If multiple rows have the same name, or if no row exists with `name`, this function returns `kHighsStatusError`.

### Parameters

  * `name`: A pointer of the name of the row to query.
  * `row`: A pointer in which to store the index of the row

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
