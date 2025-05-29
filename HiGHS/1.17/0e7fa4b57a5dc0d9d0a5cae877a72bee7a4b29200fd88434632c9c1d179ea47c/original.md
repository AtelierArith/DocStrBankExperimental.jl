```
Highs_changeColsBoundsByMask(highs, mask, lower, upper)
```

Change the variable bounds of multiple columns given by a mask.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `mask`: An array of length [num_col] with 1 if the column bounds should be changed and 0 otherwise.
  * `lower`: An array of length [num_col] with the new lower bounds.
  * `upper`: An array of length [num_col] with the new upper bounds.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
