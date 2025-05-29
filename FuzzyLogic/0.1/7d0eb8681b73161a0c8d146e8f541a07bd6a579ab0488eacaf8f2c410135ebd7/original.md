```julia
struct ProbSumAggregator <: FuzzyLogic.AbstractAggregator
```

Aggregator that combines fuzzy rules output by taking their probabilistic sum. See also [`ProbSumOr`](@ref).
