```
Highs_addLinearObjective(highs, weight, offset, coefficients, abs_tolerance, rel_tolerance, priority)
```

Adds linear objective data to HiGHS

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `weight`: The weight of the linear objective, with its positive/negative sign determining whether it is minimized or maximized during lexicographic optimization
  * `offset`: The objective offset
  * `coefficients`: A pointer to the objective coefficients
  * `abs_tolerance`: The absolute tolerance used when constructing an objective constraint during lexicographic optimization
  * `rel_tolerance`: The relative tolerance used when constructing an objective constraint during lexicographic optimization
  * `priority`: The priority of this objective during lexicographic optimization

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
