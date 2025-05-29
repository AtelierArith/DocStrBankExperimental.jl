```
CompactPerformanceEvaluation <: AbstractPerformanceEvaluation
```

Type of object returned by [`evaluate`](@ref) (for models plus data) or [`evaluate!`](@ref) (for machines) when called with the option `compact = true`. Such objects have the same structure as the [`PerformanceEvaluation`](@ref) objects returned by default, except that the following fields are omitted to save memory: `fitted_params_per_fold`, `report_per_fold`, `train_test_rows`.

For more on the remaining fields, see [`PerformanceEvaluation`](@ref).
