```
spectralradius(N::SpeciesInteractionNetwork{<:Bipartite, <:Binary}; kwargs...)
```

The bipartite version of [`spectralradius`](@ref) is measured by first projecting the bipartite network as a unipartite one using [`render`](@ref). The same options as for the unipartite version are then applied.
