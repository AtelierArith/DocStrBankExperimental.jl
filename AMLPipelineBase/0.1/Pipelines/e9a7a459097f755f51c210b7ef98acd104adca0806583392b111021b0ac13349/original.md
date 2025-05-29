```
Pipeline(machs::Vector{<:Machine},args::Dict=Dict())
```

Linear pipeline which iteratively calls and passes the result of `fit_transform` to the succeeding elements in the pipeline.

Implements `fit!` and `transform!`.
