```
JuMP.relative_gap(model::InfiniteModel)
```

Extend [`JuMP.relative_gap`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.relative_gap)  for `InfiniteModel`s in accordance with that reported by its optimizer  model. Errors if such a query is not supported or if the optimizer model  hasn't be solved.
