```
Highs_setSparseSolution(highs, num_entries, index, value)
```

Set a partial primal solution by passing values for a set of variables

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_entries`: Number of variables in the set
  * `index`: Indices of variables in the set
  * `value`: Values of variables in the set

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
