```
Highs_changeColBounds(highs, col, lower, upper)
```

Change the variable bounds of a column.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col`: The index of the column whose bounds are to change.
  * `lower`: The new lower bound.
  * `upper`: The new upper bound.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
