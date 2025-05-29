```
outcomes(o::OutcomeSpace, x)
```

Return all (unique) outcomes that appear in the (encoded) input data `x`, according to the given [`OutcomeSpace`](@ref). Equivalent to `probabilities_and_outcomes(o, x)[2]`, but for some estimators it may be explicitly extended for better performance.
