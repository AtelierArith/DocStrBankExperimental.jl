```
StopWhenStepsizeLess <: StoppingCriterion
```

stores a threshold when to stop looking at the last step size determined or found during the last iteration from within a [`AbstractManoptSolverState`](@ref).

# Constructor

```
StopWhenStepsizeLess(ε)
```

initialize the stopping criterion to a threshold `ε`.
