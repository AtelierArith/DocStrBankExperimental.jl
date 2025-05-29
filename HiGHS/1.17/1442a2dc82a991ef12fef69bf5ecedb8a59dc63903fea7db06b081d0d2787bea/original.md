```
Highs_deleteRowsBySet(highs, num_set_entries, set)
```

Delete multiple rows given by an array of indices.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_set_entries`: The number of rows to delete.
  * `set`: An array of size [num_set_entries] with the indices of the rows to delete.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
