```
JuMP.objective_bound(model::InfiniteModel)
```

Extend [`JuMP.objective_bound`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.objective_bound)  for `InfiniteModel`s in accordance with that reported by its optimizer  model. Errors if such a query is not supported or if the optimizer model  hasn't be solved.
