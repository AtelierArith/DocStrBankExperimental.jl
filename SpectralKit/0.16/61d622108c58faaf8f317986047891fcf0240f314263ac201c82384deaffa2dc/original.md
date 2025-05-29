```julia
struct InteriorGrid2 <: SpectralKit.AbstractGrid
```

Grid with interior points that results in smaller grids than `InteriorGrid` when nested. Equivalent to an `EndpointGrid` with endpoints dropped.
