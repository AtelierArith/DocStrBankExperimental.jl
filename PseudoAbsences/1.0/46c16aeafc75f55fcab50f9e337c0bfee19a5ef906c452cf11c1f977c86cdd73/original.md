```
backgroundpoints(layer::T, n::Int; kwargs...) where {T <: SimpleSDMLayer}
```

Generates background points based on a layer that gives the weight of each cell in the final sample. The additional keywords arguments are passed to `StatsBase.sample`, which is used internally. This includes the `replace` keyword to determine whether sampling should use replacement.
