```
Highs_scaleCol(highs, col, scaleval)
```

Scale a column by a constant.

Scaling a column modifies the elements in the constraint matrix, the variable bounds, and the objective coefficient.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col`: The index of the column to scale.
  * `scaleval`: The value by which to scale the column. If `scaleval < 0`, the variable bounds flipped.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
