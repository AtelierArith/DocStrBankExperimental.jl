```
topological_genome(g::Union{String,PeriodicGraph}, options::Options=Options())
topological_genome(g::Union{String,PeriodicGraph}; kwargs...)
```

Compute the topological genome of a periodic graph. If given a topological key (as a string), it is converted to a `PeriodicGraph` first.

Return a [`TopologicalGenome`](@ref).
