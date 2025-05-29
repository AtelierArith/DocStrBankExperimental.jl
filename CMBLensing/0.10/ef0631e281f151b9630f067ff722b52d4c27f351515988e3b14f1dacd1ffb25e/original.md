```
ProjEquiRect(; Ny::Int, Nx::Int, θspan::Tuple, φspan::Tuple,         T=Float32, storage=Array)
ProjEquiRect(; θ::Vector, φ::Vector, θedges::Vector, φedges::Vector, T=Float32, storage=Array)
```

Construct an EquiRect projection object. The projection can either be specified by:

  * The number of pixels `Ny` and `Nx` (corresponding to the `θ` and `φ` angular directions, respectively) and the span in radians of the field in these directions, `θspan` and `φspan`. The order in which the span tuples are given is irrelevant, either order will refer to the same field. Note, the spans correspond to the field size between outer pixel edges, not from pixel centers. If one wishes to call `Cℓ_to_Cov` with this projection, `φspan` must be an integer multiple of 2π, but other functionality will be available if this is not the case.
  * A manual list of pixels centers and pixel edges, `θ`, `φ`, `θedges`, `φedges`.
