```
Highs_deleteColsBySet(highs, num_set_entries, set)
```

Delete multiple columns given by an array of indices.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_set_entries`: The number of columns to delete.
  * `set`: An array of size [num_set_entries] with the indices of the columns to delete.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
