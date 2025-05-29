```
information_maximum(e::InformationMeasure, o::OutcomeSpace [, x])
```

Return the maximum value of the given information measure can have, given input data `x` and the given outcome space (the [`OutcomeSpace`](@ref) may also be specified by a [`ProbabilitiesEstimator`](@ref)).

Like in [`outcome_space`](@ref), for some outcome spaces, the possible outcomes are known without knowledge of input `x`, in which case the function dispatches to `information_maximum(e, o)`.

```
information_maximum(e::InformationMeasure, L::Int)
```

The same as above, but computed directly from the number of total outcomes `L`.
