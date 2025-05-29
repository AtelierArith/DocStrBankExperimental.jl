```
Highs_passLinearObjectives(highs, num_linear_objective, weight, offset, coefficients, abs_tolerance, rel_tolerance, priority)
```

Passes multiple linear objective data to HiGHS, clearing any such data already in HiGHS

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `weight`: A pointer to the weights of the linear objective, with its positive/negative sign determining whether it is minimized or maximized during lexicographic optimization
  * `offset`: A pointer to the objective offsets
  * `coefficients`: A pointer to the objective coefficients
  * `abs_tolerance`: A pointer to the absolute tolerances used when constructing objective constraints during lexicographic optimization
  * `rel_tolerance`: A pointer to the relative tolerances used when constructing objective constraints during lexicographic optimization
  * `priority`: A pointer to the priorities of the objectives during lexicographic optimization

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
