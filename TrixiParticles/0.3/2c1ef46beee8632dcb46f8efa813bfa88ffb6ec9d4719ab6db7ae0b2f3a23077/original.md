```
ComplexShape(geometry::Union{TriangleMesh, Polygon}; particle_spacing, density,
             pressure=0.0, mass=nothing, velocity=zeros(ndims(geometry)),
             point_in_geometry_algorithm=WindingNumberJacobson(; geometry,
                                                               hierarchical_winding=false,
                                                               winding_number_factor=sqrt(eps())),
             grid_offset::Real=0.0, max_nparticles=10^7,
             pad_initial_particle_grid=2particle_spacing)
```

Sample a complex geometry with particles. Returns an [`InitialCondition`](@ref). Note that an initial particle grid is generated inside the bounding box of the geometry. A `point_in_geometry_algorithm` checks if particles are inside the geometry or not. For more information about the method see [`WindingNumberJacobson`](@ref) or [`WindingNumberHormann`](@ref).

# Arguments

  * `geometry`: Geometry returned by [`load_geometry`](@ref).

# Keywords

  * `particle_spacing`:   Spacing between the particles.
  * `density`:            Either a function mapping each particle's coordinates to its density,                       or a scalar for a constant density over all particles.
  * `velocity`:           Either a function mapping each particle's coordinates to its velocity,                       or, for a constant fluid velocity, a vector holding this velocity.                       Velocity is constant zero by default.
  * `mass`:               Either `nothing` (default) to automatically compute particle mass from particle                       density and spacing, or a function mapping each particle's coordinates to its mass,                       or a scalar for a constant mass over all particles.
  * `pressure`:           Scalar to set the pressure of all particles to this value.                       This is only used by the [`EntropicallyDampedSPHSystem`](@ref) and                       will be overwritten when using an initial pressure function in the system.
  * `point_in_geometry_algorithm`: Algorithm for sampling the complex geometry with particles.                                It basically checks whether a particle is inside an object or not.                                For more information see [`WindingNumberJacobson`](@ref) or [`WindingNumberHormann`](@ref)
  * `grid_offset`: Offset of the initial particle grid of the bounding box of the `geometry`.
  * `max_nparticles`: Maximum number of particles in the initial particle grid.                   This is only used to avoid accidentally choosing a `particle_spacing`                   that is too small for the scale of the geometry.
  * `pad_initial_particle_grid`: Padding of the initial particle grid.

!!! warning "Experimental Implementation"
    This is an experimental feature and may change in any future releases.

