```
JuMP.dual_objective_value(model::InfiniteModel; [result::Int = 1])
```

Extend [`JuMP.dual_objective_value`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.dual_objective_value)  for `InfiniteModel`s in accordance with that reported by its optimizer  model and the result index `result` of the most recent solution obtained.  Errors if such a query is not supported or if the optimizer model hasn't  be solved.
