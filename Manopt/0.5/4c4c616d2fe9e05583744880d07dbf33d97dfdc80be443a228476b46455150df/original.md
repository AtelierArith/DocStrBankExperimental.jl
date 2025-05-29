```
StopWhenAll <: StoppingCriterionSet
```

store an array of [`StoppingCriterion`](@ref) elements and indicates to stop, when *all* indicate to stop. The `reason` is given by the concatenation of all reasons.

# Constructor

```
StopWhenAll(c::NTuple{N,StoppingCriterion} where N)
StopWhenAll(c::StoppingCriterion,...)
```
