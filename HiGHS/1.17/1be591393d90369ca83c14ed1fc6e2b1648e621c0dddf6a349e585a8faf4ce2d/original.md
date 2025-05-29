```
Highs_changeColsCostBySet(highs, num_set_entries, set, cost)
```

Change the cost of multiple columns given by an array of indices.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_set_entries`: The number of columns to change.
  * `set`: An array of size [num_set_entries] with the indices of the columns to change.
  * `cost`: An array of length [num_set_entries] with the new costs of the columns.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
