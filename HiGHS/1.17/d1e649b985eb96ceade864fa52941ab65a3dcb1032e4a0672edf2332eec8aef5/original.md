```
Highs_addVar(highs, lower, upper)
```

Add a new variable to the model.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `lower`: The lower bound of the column.
  * `upper`: The upper bound of the column.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
