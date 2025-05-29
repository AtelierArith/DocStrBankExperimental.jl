```
StopWhenSubgradientNormLess <: StoppingCriterion
```

A stopping criterion based on the current subgradient norm.

# Constructor

```
StopWhenSubgradientNormLess(ε::Float64)
```

Create a stopping criterion with threshold `ε` for the subgradient, that is, this criterion indicates to stop when [`get_subgradient`](@ref) returns a subgradient vector of norm less than `ε`.
