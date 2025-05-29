```
Highs_scaleRow(highs, row, scaleval)
```

Scale a row by a constant.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `row`: The index of the row to scale.
  * `scaleval`: The value by which to scale the row. If `scaleval < 0`, the row bounds are flipped.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
