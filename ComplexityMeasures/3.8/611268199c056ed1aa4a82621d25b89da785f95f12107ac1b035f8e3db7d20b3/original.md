```
probabilities(
    [est::ProbabilitiesEstimator], o::OutcomeSpace, x::Array_or_SSSet
) → p::Probabilities
```

Compute the same probabilities as in the [`probabilities_and_outcomes`](@ref) function, with two differences:

1. Do not explicitly return the outcomes.
2. If the outcomes are not estimated for free while estimating the counts, a special integer type is used to enumerate the outcomes, to avoid the computational cost of estimating the outcomes.

```
probabilities([est::ProbabilitiesEstimator], counts::Counts) → (p::Probabilities, Ω)
```

The same as above, but estimate the probability directly from a set of [`Counts`](@ref).
