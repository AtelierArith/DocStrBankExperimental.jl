```
StopWhenIterateNaN <: StoppingCriterion
```

stop looking at the cost function of the optimization problem from within a [`AbstractManoptProblem`](@ref), i.e `get_cost(p,get_iterate(o))`.

# Constructor

```
StopWhenIterateNaN()
```

initialize the stopping criterion to NaN.
