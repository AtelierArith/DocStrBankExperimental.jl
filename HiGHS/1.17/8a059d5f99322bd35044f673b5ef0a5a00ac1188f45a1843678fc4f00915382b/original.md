```
Highs_writeSolution(highs, filename)
```

Write the solution information (including dual and basis status, if available) to a file.

See also: [`Highs_writeSolutionPretty`](@ref).

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `filename`: The name of the file to write the results to.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
