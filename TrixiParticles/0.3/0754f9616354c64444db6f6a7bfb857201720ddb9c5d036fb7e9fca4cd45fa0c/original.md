```
DEMSystem(initial_condition, contact_model; damping_coefficient=0.0001,
          acceleration=ntuple(_ -> 0.0, ndims(initial_condition)), source_terms=nothing,
          radius=nothing)
```

Constructs a Discrete Element Method (DEM) system for numerically simulating the dynamics of granular and particulate matter. DEM is employed to simulate and analyze the motion, interactions, and collective behavior of assemblies of discrete, solid particles, typically under mechanical loading. The model accounts for individual particle characteristics and implements interaction laws that govern contact forces (normal and tangential), based on specified material properties and contact mechanics.

# Arguments

  * `initial_condition`: Initial condition of the system, encapsulating the initial positions,  velocities, masses, and radii of particles.
  * `contact_model`: Contact model used for particle interactions.

# Keywords

  * `acceleration`: Global acceleration vector applied to the system, such as gravity. Specified as  an `SVector` of length `NDIMS`, with a default of zero in each dimension.
  * `source_terms`: Optional; additional forces or modifications to particle dynamics not  captured by standard DEM interactions, such as electromagnetic forces or user-defined perturbations.
  * `damping_coefficient=0.0001`: Set a damping coefficient for the collision interactions.
  * `radius=nothing`: Specifies the radius of the particles, defaults to `initial_condition.particle_spacing / 2`.

!!! warning "Experimental Implementation"
    This is an experimental feature and may change in a future releases.


## References

[Bicanic2004](@cite), [Cundall1979](@cite), [DiRenzo2004](@cite)
