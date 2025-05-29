```
StopWhenAny <: StoppingCriterionSet
```

store an array of [`StoppingCriterion`](@ref) elements and indicates to stop, when *any* single one indicates to stop. The `reason` is given by the concatenation of all reasons (assuming that all non-indicating return `""`).

# Constructor

```
StopWhenAny(c::NTuple{N,StoppingCriterion} where N)
StopWhenAny(c::StoppingCriterion...)
```
