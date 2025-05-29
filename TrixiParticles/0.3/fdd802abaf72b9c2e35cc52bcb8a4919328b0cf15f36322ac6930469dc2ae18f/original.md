```
RectangularShape(particle_spacing, n_particles_per_dimension, min_coordinates;
                 velocity=zeros(length(n_particles_per_dimension)),
                 mass=nothing, density=nothing, pressure=0.0,
                 acceleration=nothing, state_equation=nothing,
                 tlsph=false, loop_order=nothing)
```

Rectangular shape filled with particles. Returns an [`InitialCondition`](@ref).

# Arguments

  * `particle_spacing`:           Spacing between the particles.
  * `n_particles_per_dimension`:  Tuple containing the number of particles in x, y and z                               (only 3D) direction, respectively.
  * `min_coordinates`:            Coordinates of the corner in negative coordinate directions.

# Keywords

  * `velocity`:       Either a function mapping each particle's coordinates to its velocity,                   or, for a constant fluid velocity, a vector holding this velocity.                   Velocity is constant zero by default.
  * `mass`:           Either `nothing` (default) to automatically compute particle mass from particle                   density and spacing, or a function mapping each particle's coordinates to its mass,                   or a scalar for a constant mass over all particles.
  * `density`:        Either a function mapping each particle's coordinates to its density,                   or a scalar for a constant density over all particles.                   Obligatory when not using a state equation. Cannot be used together with                   `state_equation`.
  * `pressure`:       Scalar to set the pressure of all particles to this value.                   This is only used by the [`EntropicallyDampedSPHSystem`](@ref) and                   will be overwritten when using an initial pressure function in the system.                   Cannot be used together with hydrostatic pressure gradient.
  * `acceleration`:   In order to initialize particles with a hydrostatic pressure gradient,                   an acceleration vector can be passed. Note that only accelerations                   in one coordinate direction and no diagonal accelerations are supported.                   This will only change the pressure of the particles. When using the                   [`WeaklyCompressibleSPHSystem`](@ref), pass a `state_equation` as well                   to initialize the particles with the corresponding density and mass.                   When using the [`EntropicallyDampedSPHSystem`](@ref), the pressure                   will be overwritten when using an initial pressure function in the system.                   This cannot be used together with the `pressure` keyword argument.
  * `state_equation`: When calculating a hydrostatic pressure gradient by setting `acceleration`,                   the `state_equation` will be used to set the corresponding density.                   Cannot be used together with `density`.
  * `tlsph`:          With the [`TotalLagrangianSPHSystem`](@ref), particles need to be placed                   on the boundary of the shape and not one particle radius away, as for fluids.                   When `tlsph=true`, particles will be placed on the boundary of the shape.
  * `coordinates_perturbation`: Add a small random displacement to the particle positions,                             where the amplitude is `coordinates_perturbation * particle_spacing`.

# Examples

```jldoctest; output = false, setup = :(particle_spacing = 0.1)
# 2D
rectangular = RectangularShape(particle_spacing, (5, 4), (1.0, 2.0), density=1000.0)

# 2D with hydrostatic pressure gradient.
# `state_equation` has to be the same as for the WCSPH system.
state_equation = StateEquationCole(sound_speed=20.0, exponent=7, reference_density=1000.0)
rectangular = RectangularShape(particle_spacing, (5, 4), (1.0, 2.0),
                               acceleration=(0.0, -9.81), state_equation=state_equation)

# 3D
rectangular = RectangularShape(particle_spacing, (5, 4, 7), (1.0, 2.0, 3.0), density=1000.0)

# output
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ InitialCondition{Float64}                                                                        │
│ ═════════════════════════                                                                        │
│ #dimensions: ……………………………………………… 3                                                                │
│ #particles: ………………………………………………… 140                                                              │
│ particle spacing: ………………………………… 0.1                                                              │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
