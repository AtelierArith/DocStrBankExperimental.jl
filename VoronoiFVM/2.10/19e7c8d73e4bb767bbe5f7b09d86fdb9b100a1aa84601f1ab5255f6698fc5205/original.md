```julia
edgevelocities(grid, velofunc; kwargs...)

```

Project velocity onto grid edges. That is, we compute the path integrals of the given `velofunc` along the  Voronoi cell edges as provided by [`integrate`](@ref).
