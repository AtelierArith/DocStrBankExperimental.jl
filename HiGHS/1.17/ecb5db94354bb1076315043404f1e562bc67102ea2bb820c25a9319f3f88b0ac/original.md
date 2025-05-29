```
Highs_deleteColsByMask(highs, mask)
```

Delete multiple columns given by a mask.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `mask`: An array of length [num_col] with 1 if the column should be deleted and 0 otherwise.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
