```
OpenBoundarySPHSystem(boundary_zone::BoundaryZone;
                      fluid_system::FluidSystem, buffer_size::Integer,
                      boundary_model,
                      reference_velocity=nothing,
                      reference_pressure=nothing,
                      reference_density=nothing)
```

Open boundary system for in- and outflow particles.

# Arguments

  * `boundary_zone`: See [`BoundaryZone`](@ref).

# Keywords

  * `fluid_system`: The corresponding fluid system
  * `boundary_model`: Boundary model (see [Open Boundary Models](@ref open_boundary_models))
  * `buffer_size`: Number of buffer particles.
  * `reference_velocity`: Reference velocity is either a function mapping each particle's coordinates                       and time to its velocity, an array where the $i$-th column holds                       the velocity of particle $i$ or, for a constant fluid velocity,                       a vector holding this velocity.
  * `reference_pressure`: Reference pressure is either a function mapping each particle's coordinates                       and time to its pressure, a vector holding the pressure of each particle,                       or a scalar for a constant pressure over all particles.
  * `reference_density`: Reference density is either a function mapping each particle's coordinates                      and time to its density, a vector holding the density of each particle,                      or a scalar for a constant density over all particles.

!!! note
    When using the [`BoundaryModelTafuni()`](@ref), the reference values (`reference_velocity`, `reference_pressure`, `reference_density`) can also be set to `nothing` since this model allows for either assigning physical quantities a priori or extrapolating them from the fluid domaim to the buffer zones (inflow and outflow) using ghost nodes.


!!! warning "Experimental Implementation"
    This is an experimental feature and may change in any future releases.

