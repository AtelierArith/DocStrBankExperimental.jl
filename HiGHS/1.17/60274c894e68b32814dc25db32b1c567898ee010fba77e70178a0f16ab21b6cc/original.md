```
Highs_clearModel(highs)
```

Remove all variables and constraints from the model `highs`, but do not invalidate the pointer `highs`. Future calls (for example, adding new variables and constraints) are allowed.

### Parameters

  * `highs`: A pointer to the Highs instance.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
