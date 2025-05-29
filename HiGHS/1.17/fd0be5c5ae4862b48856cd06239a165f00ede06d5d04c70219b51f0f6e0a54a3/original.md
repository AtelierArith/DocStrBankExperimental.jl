```
Highs_writeOptionsDeviations(highs, filename)
```

Write the value of non-default options to file.

This is similar to [`Highs_writeOptions`](@ref), except only options with non-default value are written to `filename`.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `filename`: The filename to write the options to.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
