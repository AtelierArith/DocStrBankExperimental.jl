```
JuMP.barrier_iterations(model::InfiniteModel)
```

Extend [`JuMP.barrier_iterations`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.barrier_iterations)  for `InfiniteModel`s in accordance with that reported by its optimizer  model. Errors if such a query is not supported or if the optimizer model  hasn't be solved.
