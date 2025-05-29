```
Highs_getColByName(highs, name, col)
```

Get the index of a column from its name.

If multiple columns have the same name, or if no column exists with `name`, this function returns `kHighsStatusError`.

### Parameters

  * `name`: A pointer of the name of the column to query.
  * `col`: A pointer in which to store the index of the column

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
