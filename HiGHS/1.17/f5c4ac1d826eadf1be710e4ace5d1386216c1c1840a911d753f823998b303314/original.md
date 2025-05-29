```
Highs_changeObjectiveSense(highs, sense)
```

Change the objective sense of the model.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `sense`: The new optimization sense in the form of a `kHighsObjSense` constant.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
