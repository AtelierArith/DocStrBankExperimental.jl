```
DG(; basis, mortar, surface_integral, volume_integral)
```

Create a discontinuous Galerkin method. If [`basis isa LobattoLegendreBasis`](@ref LobattoLegendreBasis), this creates a [`DGSEM`](@ref).
