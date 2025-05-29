```
JuMP.solve_time(model::InfiniteModel)
```

Extend [`JuMP.solve_time`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.solve_time)  for `InfiniteModel`s in accordance with that reported by its optimizer  model. Errors if such a query is not supported or if the optimizer model  hasn't be solved.
