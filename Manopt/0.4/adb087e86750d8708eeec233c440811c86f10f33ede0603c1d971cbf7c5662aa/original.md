```
StopWhenEvolutionStagnates{TParam<:Real} <: StoppingCriterion
```

The best and median fitness in each iteration is tracked over the last 20% but at least `min_size` and no more than `max_size` iterations. Solver is stopped if in both histories the median of the most recent `fraction` of values is not better than the median of the oldest `fraction`.
