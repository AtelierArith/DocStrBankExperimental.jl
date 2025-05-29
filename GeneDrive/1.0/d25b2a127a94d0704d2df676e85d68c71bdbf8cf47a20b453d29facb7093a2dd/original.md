```
Release(node::Node, organism, stage::Type{T}, gene, times::Vector, variable_release::Vector{Float64}) where T <: LifeStage
```

Return `Release` object specifying details of biological control intervention where release size is variable over time.
