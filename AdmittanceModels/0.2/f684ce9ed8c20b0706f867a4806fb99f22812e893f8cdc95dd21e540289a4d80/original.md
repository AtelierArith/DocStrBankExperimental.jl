```
Circuit(comp::SeriesComponent)
Circuit(comp::ParallelComponent)
Circuit(comp::TransmissionLine, vertex_prefix::AbstractString,
    stages_per_segment::Union{Nothing, AbstractVector{Int}}=nothing)
```

Create a Circuit for a CircuitComponent.
