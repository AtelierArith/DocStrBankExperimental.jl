```
BoundaryModelMonaghanKajtar(K, beta, boundary_particle_spacing, mass;
                            viscosity=nothing)
```

Boundary model for `BoundarySPHSystem`.

# Arguments

  * `K`: Scaling factor for repulsive force.
  * `beta`: Ratio of fluid particle spacing to boundary particle spacing.
  * `boundary_particle_spacing`: Boundary particle spacing.
  * `mass`: Vector holding the mass of each boundary particle.

# Keywords

  * `viscosity`:  Free-slip (default) or no-slip condition. See description above for further               information.
