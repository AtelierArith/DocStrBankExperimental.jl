```
Highs_changeColsBoundsBySet(highs, num_set_entries, set, lower, upper)
```

Change the bounds of multiple columns given by an array of indices.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_set_entries`: The number of columns to change.
  * `set`: An array of size [num_set_entries] with the indices of the columns to change.
  * `lower`: An array of length [num_set_entries] with the new lower bounds.
  * `upper`: An array of length [num_set_entries] with the new upper bounds.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
