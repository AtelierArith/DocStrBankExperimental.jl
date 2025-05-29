```
counts(o::OutcomeSpace, x) → cts::Counts
```

Compute the same counts as in the [`counts_and_outcomes`](@ref) function, with two differences:

1. Do not explicitly return the outcomes.
2. If the outcomes are not estimated for free while estimating the counts, a special integer type is used to enumerate the outcomes, to avoid the computational cost of estimating the outcomes.
