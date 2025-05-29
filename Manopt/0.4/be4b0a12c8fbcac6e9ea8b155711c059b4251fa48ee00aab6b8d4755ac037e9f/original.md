```
StopWhenCostLess <: StoppingCriterion
```

store a threshold when to stop looking at the cost function of the optimization problem from within a [`AbstractManoptProblem`](@ref), i.e `get_cost(p,get_iterate(o))`.

# Constructor

```
StopWhenCostLess(ε)
```

initialize the stopping criterion to a threshold `ε`.
