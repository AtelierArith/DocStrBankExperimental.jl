```
StoppingCriterionGroup <: StoppingCriterion
```

An abstract type for a Stopping Criterion that itself consists of a set of Stopping criteria. In total it acts as a stopping criterion itself. Examples are [`StopWhenAny`](@ref) and [`StopWhenAll`](@ref) that can be used to combine stopping criteria.
