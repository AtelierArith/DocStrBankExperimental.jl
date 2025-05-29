```
JuMP.node_count(model::InfiniteModel)
```

Extend [`JuMP.node_count`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.node_count)  for `InfiniteModel`s in accordance with that reported by its optimizer  model. Errors if such a query is not supported or if the optimizer model  hasn't be solved.
