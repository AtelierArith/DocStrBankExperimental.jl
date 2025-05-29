```julia
numanode(i::Integer) -> NUMA.NUMANode

```

Returns an array initializer that represents a specific NUMA node. To be used as, e.g., `Vector{Float64}(numanode(1), 1024)`.
