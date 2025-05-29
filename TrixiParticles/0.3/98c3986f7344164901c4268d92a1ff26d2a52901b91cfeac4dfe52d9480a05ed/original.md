```
sample_boundary(signed_distance_field::SignedDistanceField;
                boundary_thickness::Real, tlsph=true)
```

Sample boundary particles of a complex geometry by using the [`SignedDistanceField`](@ref) of the geometry.

# Arguments

  * `signed_distance_field`: The signed distance field of a geometry (see [`SignedDistanceField`](@ref)).

# Keywords

  * `boundary_thickness`: Thickness of the boundary
  * `tlsph`             : When `tlsph=true`, boundary particles will be placed                       one particle spacing from the surface of the geometry.                       Otherwise when `tlsph=true` (simulating fluid particles),                       boundary particles will be placed half particle spacing away from the surface.

# Examples

```jldoctest; output = false, setup = :(particle_spacing = 0.03; boundary_thickness = 4 * particle_spacing; file = joinpath(pkgdir(TrixiParticles, "examples", "preprocessing", "data"), "circle.asc"))
geometry = load_geometry(file)

signed_distance_field = SignedDistanceField(geometry, particle_spacing;
                                            use_for_boundary_packing=true,
                                            max_signed_distance=boundary_thickness)

boundary_sampled = sample_boundary(signed_distance_field; boundary_density=1.0,
                                   boundary_thickness)

# output
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ InitialCondition{Float64}                                                                        │
│ ═════════════════════════                                                                        │
│ #dimensions: ……………………………………………… 2                                                                │
│ #particles: ………………………………………………… 889                                                              │
│ particle spacing: ………………………………… 0.03                                                             │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
