```
upper(p::OrthogonalIntervalProbabilities, l)
```

Return the upper bound transition probabilities from a source state or source/action pair to a target state.

!!! note
    It is not recommended to use this function for the hot loop of O-maximization. Because the [`IntervalProbabilities`](@ref) stores the lower and gap transition probabilities, fetching the upper bound requires allocation and computation.

