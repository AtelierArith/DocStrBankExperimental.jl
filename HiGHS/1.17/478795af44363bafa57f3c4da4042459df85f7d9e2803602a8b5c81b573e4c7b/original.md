```
Highs_changeColsIntegralityBySet(highs, num_set_entries, set, integrality)
```

Change the integrality of multiple columns given by an array of indices.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_set_entries`: The number of columns to change.
  * `set`: An array of size [num_set_entries] with the indices of the columns to change.
  * `integrality`: An array of length [num_set_entries] with the new integralities of the columns in the form of `kHighsVarType` constants.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
