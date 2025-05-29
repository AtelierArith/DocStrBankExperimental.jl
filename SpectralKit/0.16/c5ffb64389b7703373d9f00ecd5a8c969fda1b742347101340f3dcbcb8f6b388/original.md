```julia
struct EndpointGrid <: SpectralKit.AbstractGrid
```

Grid that includes endpoints (eg Gauss-Lobatto).

!!! note
    For small dimensions may fall back to a grid that does not contain endpoints.

