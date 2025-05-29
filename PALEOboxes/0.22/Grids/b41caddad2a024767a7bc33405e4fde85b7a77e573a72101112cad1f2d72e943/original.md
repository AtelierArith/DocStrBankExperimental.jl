```
AbstractMesh
```

Defines additional geometric and topological information for [`PB.Domain`](@ref)

Concrete subtypes should implement methods:

[`available_spaces`](@ref) tuple of [`PB.AbstractSpace`](@ref) types supported. 

[`PB.has_internal_cartesian`](@ref) `true` if subtype uses an internal spatial representation that differs from  the external (cartesian) representation.

[`PB.get_dimensions`](@ref)

[`PB.internal_size`](@ref), optionally [`PB.cartesian_size`](@ref)

[`PB.Grids.set_subdomain!`](@ref), [`PB.Grids.get_subdomain`](@ref)

[`PB.Grids.create_default_cellrange`](@ref)

# Internal and cartesian representations

If a subtype uses an internal representation that differs from the external (cartesian) representation, it should define [`PB.has_internal_cartesian`](@ref) `true` and implement [`cartesian_to_internal`](@ref), [`internal_to_cartesian`](@ref), and [`PB.cartesian_size`](@ref).
