```
SphereShape(particle_spacing, radius, center_position, density;
            sphere_type=VoxelSphere(), n_layers=-1, layer_outwards=false,
            cutout_min=(0.0, 0.0), cutout_max=(0.0, 0.0), tlsph=false,
            velocity=zeros(length(center_position)), mass=nothing, pressure=0.0)
```

Generate a sphere that is either completely filled (by default) or hollow (by passing `n_layers`).

With the sphere type [`VoxelSphere`](@ref), a sphere of voxels (where particles are placed in the voxel center) with a regular inner structure but corners on the surface is created. Essentially, a grid of particles is generated and all particles outside the sphere are removed. With the sphere type [`RoundSphere`](@ref), a perfectly round sphere with an imperfect inner structure is created.

A cuboid can be cut out of the sphere by specifying the two corners in negative and positive coordinate directions as `cutout_min` and `cutout_max`.

# Arguments

  * `particle_spacing`:   Spacing between the particles.
  * `radius`:             Radius of the sphere.
  * `center_position`:    The coordinates of the center of the sphere.
  * `density`:            Either a function mapping each particle's coordinates to its density,                       or a scalar for a constant density over all particles.

# Keywords

  * `sphere_type`:    Either [`VoxelSphere`](@ref) or [`RoundSphere`](@ref) (see                   explanation above).
  * `n_layers`:       Set to an integer greater than zero to generate a hollow sphere,                   where the shell consists of `n_layers` layers.
  * `layer_outwards`: When set to `false` (by default), `radius` is the outer radius                   of the sphere. When set to `true`, `radius` is the inner radius                   of the sphere. This is only used when `n_layers > 0`.
  * `cutout_min`:     Corner in negative coordinate directions of a cuboid that is to be                   cut out of the sphere.
  * `cutout_max`:     Corner in positive coordinate directions of a cuboid that is to be                   cut out of the sphere.
  * `tlsph`:          With the [`TotalLagrangianSPHSystem`](@ref), particles need to be placed                   on the boundary of the shape and not one particle radius away, as for fluids.                   When `tlsph=true`, particles will be placed on the boundary of the shape.
  * `velocity`:   Either a function mapping each particle's coordinates to its velocity,               or, for a constant fluid velocity, a vector holding this velocity.               Velocity is constant zero by default.
  * `mass`:       Either `nothing` (default) to automatically compute particle mass from particle               density and spacing, or a function mapping each particle's coordinates to its mass,               or a scalar for a constant mass over all particles.
  * `pressure`:   Either a function mapping each particle's coordinates to its pressure,               or a scalar for a constant pressure over all particles. This is optional and               only needed when using the [`EntropicallyDampedSPHSystem`](@ref).

# Examples

```jldoctest; output = false
# Filled circle with radius 0.5, center in (0.2, 0.4) and a particle spacing of 0.1
SphereShape(0.1, 0.5, (0.2, 0.4), 1000.0)

# Same as before, but perfectly round
SphereShape(0.1, 0.5, (0.2, 0.4), 1000.0, sphere_type=RoundSphere())

# Hollow circle with ~3 layers, outer radius 0.5, center in (0.2, 0.4) and a particle
# spacing of 0.1.
SphereShape(0.1, 0.5, (0.2, 0.4), 1000.0, n_layers=3)

# Same as before, but perfectly round
SphereShape(0.1, 0.5, (0.2, 0.4), 1000.0, n_layers=3, sphere_type=RoundSphere())

# Hollow circle with 3 layers, inner radius 0.5, center in (0.2, 0.4) and a particle spacing
# of 0.1.
SphereShape(0.1, 0.5, (0.2, 0.4), 1000.0, n_layers=3, layer_outwards=true)

# Filled circle with radius 0.1, center in (0.0, 0.0), particle spacing 0.1, but the
# rectangle [0, 1] x [-0.2, 0.2] is cut out.
SphereShape(0.1, 1.0, (0.0, 0.0), 1000.0, cutout_min=(0.0, -0.2), cutout_max=(1.0, 0.2))

# Filled 3D sphere with radius 0.5, center in (0.2, 0.4, 0.3) and a particle spacing of 0.1
SphereShape(0.1, 0.5, (0.2, 0.4, 0.3), 1000.0)

# Same as before, but perfectly round
SphereShape(0.1, 0.5, (0.2, 0.4, 0.3), 1000.0, sphere_type=RoundSphere())

# output
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ InitialCondition{Float64}                                                                        │
│ ═════════════════════════                                                                        │
│ #dimensions: ……………………………………………… 3                                                                │
│ #particles: ………………………………………………… 518                                                              │
│ particle spacing: ………………………………… 0.1                                                              │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
