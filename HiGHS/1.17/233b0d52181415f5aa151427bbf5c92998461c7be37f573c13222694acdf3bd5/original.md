```
Highs_changeColsIntegralityByMask(highs, mask, integrality)
```

Change the integrality of multiple columns given by a mask.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `mask`: An array of length [num_col] with 1 if the column integrality should be changed and 0 otherwise.
  * `integrality`: An array of length [num_col] with the new integralities of the columns in the form of `kHighsVarType` constants.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
