```
Highs_changeColsCostByMask(highs, mask, cost)
```

Change the cost of multiple columns given by a mask.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `mask`: An array of length [num_col] with 1 if the column cost should be changed and 0 otherwise.
  * `cost`: An array of length [num_col] with the new costs.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
