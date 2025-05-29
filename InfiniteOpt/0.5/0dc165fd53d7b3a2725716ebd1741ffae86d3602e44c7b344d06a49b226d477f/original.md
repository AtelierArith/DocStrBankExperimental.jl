```
JuMP.has_duals(model::InfiniteModel; [result::Int = 1])
```

Extend [`JuMP.has_duals`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.has_duals)  for `InfiniteModel`s in accordance with that reported by its optimizer  model and the result index `result` of the most recent solution obtained.  Errors if such a query is not supported or if the optimizer model hasn't  be solved.
