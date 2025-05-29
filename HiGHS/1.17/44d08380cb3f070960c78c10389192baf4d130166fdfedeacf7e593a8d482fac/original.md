```
Highs_changeRowBounds(highs, row, lower, upper)
```

Change the bounds of a row.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `row`: The index of the row whose bounds are to change.
  * `lower`: The new lower bound.
  * `upper`: The new upper bound.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
