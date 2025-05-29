```
StopWhenPollSizeLess <: StoppingCriterion
```

stores a threshold when to stop looking at the poll mesh size of an [`MeshAdaptiveDirectSearchState`](@ref).

# Constructor

```
StopWhenPollSizeLess(ε)
```

initialize the stopping criterion to a threshold `ε`.
