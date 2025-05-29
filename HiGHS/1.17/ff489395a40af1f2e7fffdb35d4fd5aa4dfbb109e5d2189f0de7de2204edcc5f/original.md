```
Highs_writeSolutionPretty(highs, filename)
```

Write the solution information (including dual and basis status, if available) to a file in a human-readable format.

The method identical to [`Highs_writeSolution`](@ref), except that the printout is in a human-readable format.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `filename`: The name of the file to write the results to.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
