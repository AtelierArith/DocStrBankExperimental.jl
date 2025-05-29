```
missing_probabilities([est::ProbabilitiesEstimator], o::OutcomeSpace, x)
```

Same as [`missing_outcomes`](@ref), but defines a "missing outcome" as an outcome having 0 probability according to `est`.
