```
function expec_series_err
```

Convenience method to estimate the sampling error in the ensemble solution

# Arguments

  * `sim`: EnsembleSolution, result of calling `emulate`
  * `index`: index of the expectation value in the array provided
  * `factor`: How many σ from the mean to report
