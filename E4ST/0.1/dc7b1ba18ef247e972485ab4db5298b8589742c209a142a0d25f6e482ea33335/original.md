```
compute_result(data, table_name, result_name, idxs=(:), yr_idxs=(:), hr_idxs=(:))
```

Computes result `result_name` for table `table_name` for table indexes `idxs`, year indexes `yr_idxs` and hour indexes `hr_idxs`.  See [`add_results_formula!`](@ref) to add other results formulas for computing results.

Note that this will recursively compute results for any derived result, as needed.

If any result is computed to be `NaN`, returns `0.0` instead, so that the NaN does not "infect" other results.
