```
total_outcomes(o::OutcomeSpace, x)
```

Return the length (cardinality) of the outcome space $\Omega$ of `est`.

For some [`OutcomeSpace`](@ref), the cardinality is known without knowledge of input `x`, in which case the function dispatches to `total_outcomes(est)`. In general it is recommended to use the 2-argument version irrespectively of estimator.
