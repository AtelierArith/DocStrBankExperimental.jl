```
InitialCondition(; coordinates, density, velocity=zeros(size(coordinates, 1)),
                 mass=nothing, pressure=0.0, particle_spacing=-1.0)
```

Struct to hold the initial configuration of the particles.

The following setups return `InitialCondition`s for commonly used setups:

  * [`RectangularShape`](@ref)
  * [`SphereShape`](@ref)
  * [`RectangularTank`](@ref)
  * [`ComplexShape`](@ref)
  * [`extrude_geometry`](@ref)

`InitialCondition`s support the set operations `union`, `setdiff` and `intersect` in order to build more complex geometries. `InitialCondition`s also support the set operations `setdiff` and `intersect` together with `TrixiParticles.TriangleMesh` and `TrixiParticles.Polygon` returned by [`load_geometry`](@ref).

# Arguments

  * `coordinates`: An array where the $i$-th column holds the coordinates of particle $i$.
  * `density`:     Either a vector holding the density of each particle,                or a function mapping each particle's coordinates to its density,                or a scalar for a constant density over all particles.

# Keywords

  * `velocity`:   Either an array where the $i$-th column holds the velocity of particle $i$,               or a function mapping each particle's coordinates to its velocity,               or, for a constant fluid velocity, a vector holding this velocity.               Velocity is constant zero by default.
  * `mass`:       Either `nothing` (default) to automatically compute particle mass from particle               density and spacing, or a vector holding the mass of each particle,               or a function mapping each particle's coordinates to its mass,               or a scalar for a constant mass over all particles.
  * `pressure`:   Either a vector holding the pressure of each particle,               or a function mapping each particle's coordinates to its pressure,               or a scalar for a constant pressure over all particles. This is optional and               only needed when using the [`EntropicallyDampedSPHSystem`](@ref).
  * `particle_spacing`: The spacing between the particles. This is a scalar, as the spacing                     is assumed to be uniform. This is only needed when using                     set operations on the `InitialCondition` or for automatic mass calculation.

# Examples

```jldoctest; output = false
# Rectangle filled with particles
initial_condition = RectangularShape(0.1, (3, 4), (-1.0, 1.0), density=1.0)

# Two spheres in one initial condition
initial_condition = union(SphereShape(0.15, 0.5, (-1.0, 1.0), 1.0),
                          SphereShape(0.15, 0.2, (0.0, 1.0), 1.0))

# Rectangle with a spherical hole
shape1 = RectangularShape(0.1, (16, 13), (-0.8, 0.0), density=1.0)
shape2 = SphereShape(0.1, 0.35, (0.0, 0.6), 1.0, sphere_type=RoundSphere())
initial_condition = setdiff(shape1, shape2)

# Intersect of a rectangle with a sphere. Note that this keeps the particles of the
# rectangle that are in the intersect, while `intersect(shape2, shape1)` would consist of
# the particles of the sphere that are in the intersect.
shape1 = RectangularShape(0.1, (16, 13), (-0.8, 0.0), density=1.0)
shape2 = SphereShape(0.1, 0.35, (0.0, 0.6), 1.0, sphere_type=RoundSphere())
initial_condition = intersect(shape1, shape2)

# Set operations with geometries loaded from files
shape = RectangularShape(0.05, (20, 20), (0.0, 0.0), density=1.0)
file =  pkgdir(TrixiParticles, "examples", "preprocessing", "data", "circle.asc")
geometry = load_geometry(file)

initial_condition_1 = intersect(shape, geometry)
initial_condition_2 = setdiff(shape, geometry)

# Build `InitialCondition` manually
coordinates = [0.0 1.0 1.0
               0.0 0.0 1.0]
velocity = zero(coordinates)
mass = ones(3)
density = 1000 * ones(3)
initial_condition = InitialCondition(; coordinates, velocity, mass, density)

# With functions
initial_condition = InitialCondition(; coordinates, velocity=x -> 2x, mass=1.0, density=1000.0)

# output
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ InitialCondition{Float64}                                                                        │
│ ═════════════════════════                                                                        │
│ #dimensions: ……………………………………………… 2                                                                │
│ #particles: ………………………………………………… 3                                                                │
│ particle spacing: ………………………………… -1.0                                                             │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
