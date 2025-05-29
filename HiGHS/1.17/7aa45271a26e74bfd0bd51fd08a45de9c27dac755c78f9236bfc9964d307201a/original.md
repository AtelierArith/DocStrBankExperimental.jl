```
Highs_changeRowsBoundsByMask(highs, mask, lower, upper)
```

Change the bounds of multiple rows given by a mask.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `mask`: An array of length [num_row] with 1 if the row bounds should be changed and 0 otherwise.
  * `lower`: An array of length [num_row] with the new lower bounds.
  * `upper`: An array of length [num_row] with the new upper bounds.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
