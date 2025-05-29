```
allprobabilities_and_outcomes(est::ProbabilitiesEstimator, x::Array_or_SSSet) → (p::Probabilities, outs)
allprobabilities_and_outcomes(o::OutcomeSpace, x::Array_or_SSSet) → (p::Probabilities, outs)
```

The same as [`probabilities_and_outcomes`](@ref), but ensures that outcomes with `0` probability are explicitly added in the returned vector. This means that `p[i]` is the probability of `ospace[i]`, with `ospace =`[`outcome_space`](@ref)`(est, x)`.

This function is useful in cases where one wants to compare the probability mass functions of two different input data `x, y` under the same estimator. E.g., to compute the KL-divergence of the two PMFs assumes that the obey the same indexing. This is not true for [`probabilities`](@ref) even with the same `est`, due to the skipping of 0 entries, but it is true for [`allprobabilities_and_outcomes`](@ref).
