```
RectangularTank(particle_spacing, fluid_size, tank_size, fluid_density;
                velocity=zeros(length(fluid_size)), fluid_mass=nothing,
                pressure=0.0,
                acceleration=nothing, state_equation=nothing,
                boundary_density=fluid_density,
                n_layers=1, spacing_ratio=1.0,
                min_coordinates=zeros(length(fluid_size)),
                faces=Tuple(trues(2 * length(fluid_size))))
```

Rectangular tank filled with a fluid to set up dam-break-style simulations.

# Arguments

  * `particle_spacing`:   Spacing between the fluid particles.
  * `fluid_size`:         The dimensions of the fluid as `(x, y)` (or `(x, y, z)` in 3D).
  * `tank_size`:          The dimensions of the tank as `(x, y)` (or `(x, y, z)` in 3D).
  * `fluid_density`:      The rest density of the fluid. Will only be used as default for                       `boundary_density` when using a state equation.

# Keywords

  * `velocity`:       Either a function mapping each particle's coordinates to its velocity,                   or, for a constant fluid velocity, a vector holding this velocity.                   Velocity is constant zero by default.
  * `fluid_mass`:     Either `nothing` (default) to automatically compute particle mass from particle                   density and spacing, or a function mapping each particle's coordinates to its mass,                   or a scalar for a constant mass over all particles.
  * `pressure`:       Scalar to set the pressure of all particles to this value.                   This is only used by the [`EntropicallyDampedSPHSystem`](@ref) and                   will be overwritten when using an initial pressure function in the system.                   Cannot be used together with hydrostatic pressure gradient.
  * `acceleration`:   In order to initialize particles with a hydrostatic pressure gradient,                   an acceleration vector can be passed. Note that only accelerations                   in one coordinate direction and no diagonal accelerations are supported.                   This will only change the pressure of the particles. When using the                   [`WeaklyCompressibleSPHSystem`](@ref), pass a `state_equation` as well                   to initialize the particles with the corresponding density and mass.                   When using the [`EntropicallyDampedSPHSystem`](@ref), the pressure                   will be overwritten when using an initial pressure function in the system.                   This cannot be used together with the `pressure` keyword argument.
  * `state_equation`: When calculating a hydrostatic pressure gradient by setting `acceleration`,                   the `state_equation` will be used to set the corresponding density.                   Cannot be used together with `density`.
  * `boundary_density`:   Density of each boundary particle (by default set to the fluid density)
  * `n_layers`:           Number of boundary layers.
  * `spacing_ratio`:      Ratio of `particle_spacing` to boundary particle spacing.                       A value of 2 means that the boundary particle spacing will be                       half the fluid particle spacing.
  * `min_coordinates`:    Coordinates of the corner in negative coordinate directions.
  * `faces`:              By default all faces are generated. Set faces by passing a                       bit-array of length 4 (2D) or 6 (3D) to generate the faces in the                       normal direction: -x,+x,-y,+y,-z,+z.

# Fields

  * `fluid::InitialCondition`:    [`InitialCondition`](@ref) for the fluid.
  * `boundary::InitialCondition`: [`InitialCondition`](@ref) for the boundary.
  * `fluid_size::Tuple`:          Tuple containing the size of the fluid in each dimension after rounding.
  * `tank_size::Tuple`:           Tuple containing the size of the tank in each dimension after rounding.

# Examples

```jldoctest; output = false, filter = r"RectangularTank.*", setup = :(particle_spacing = 0.1; water_width = water_depth = container_width = container_height = container_depth = 1.0; water_height = 0.5; fluid_density = 1000.0)
# 2D
setup = RectangularTank(particle_spacing, (water_width, water_height),
                        (container_width, container_height), fluid_density,
                        n_layers=2, spacing_ratio=3)

# 2D with hydrostatic pressure gradient.
# `state_equation` has to be the same as for the WCSPH system.
state_equation = StateEquationCole(sound_speed=10.0, exponent=1, reference_density=1000.0)
setup = RectangularTank(particle_spacing, (water_width, water_height),
                        (container_width, container_height), fluid_density,
                        acceleration=(0.0, -9.81), state_equation=state_equation)

# 3D
setup = RectangularTank(particle_spacing, (water_width, water_height, water_depth),
                        (container_width, container_height, container_depth), fluid_density,
                        n_layers=2)

# output
RectangularTank{3, 6, Float64}(...) *the rest of this line is ignored by filter*
```

See also: [`reset_wall!`](@ref).
