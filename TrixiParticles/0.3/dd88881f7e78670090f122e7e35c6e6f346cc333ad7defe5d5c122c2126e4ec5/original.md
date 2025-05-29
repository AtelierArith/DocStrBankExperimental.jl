```
SignedDistanceField(geometry, particle_spacing;
                    points=nothing,
                    max_signed_distance=4 * particle_spacing,
                    use_for_boundary_packing=false)
```

Generate particles along a surface of a complex geometry storing the signed distances and normals to this surface.

# Arguments

  * `geometry`: Geometry returned by [`load_geometry`](@ref).
  * `particle_spacing`: Spacing between the particles.

# Keywords

  * `max_signed_distance`:      Maximum signed distance to be stored. That is, only particles with a                             distance of `abs(max_signed_distance)` to the surface of the shape                             will be sampled.
  * `points`:                   Points on which the signed distance is computed.                             When set to `nothing` (default), the bounding box of the shape will be                             sampled with a uniform grid of points.
  * `use_for_boundary_packing`: Set to `true` if [`SignedDistanceField`] is used to pack                             a boundary [`ParticlePackingSystem`](@ref).                             Use the default of `false` when packing without a boundary.
