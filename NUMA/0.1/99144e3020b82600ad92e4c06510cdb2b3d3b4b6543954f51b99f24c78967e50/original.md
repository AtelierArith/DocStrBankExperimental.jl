```julia
numalocal() -> NUMA.NUMALocal

```

Returns an array initializer that represents the local NUMA node. To be used as, e.g., `Vector{Float64}(numalocal(), 1024)`.
