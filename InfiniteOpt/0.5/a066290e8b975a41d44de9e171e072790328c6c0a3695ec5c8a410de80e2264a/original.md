```
JuMP.termination_status(model::InfiniteModel)
```

Extend [`JuMP.termination_status`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.termination_status)  for `InfiniteModel`s in accordance with that reported by its optimizer  model. Errors if such a query is not supported or if the optimizer model  hasn't be solved.
