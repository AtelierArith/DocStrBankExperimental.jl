```
EntropicallyDampedSPHSystem(initial_condition, smoothing_kernel,
                            smoothing_length, sound_speed;
                            pressure_acceleration=inter_particle_averaged_pressure,
                            density_calculator=SummationDensity(),
                            transport_velocity=nothing,
                            alpha=0.5, viscosity=nothing,
                            acceleration=ntuple(_ -> 0.0, NDIMS), surface_tension=nothing,
                            surface_normal_method=nothing, buffer_size=nothing,
                            reference_particle_spacing=0.0, source_terms=nothing)
```

System for particles of a fluid. As opposed to the [weakly compressible SPH scheme](@ref wcsph), which uses an equation of state, this scheme uses a pressure evolution equation to calculate the pressure. See [Entropically Damped Artificial Compressibility for SPH](@ref edac) for more details on the method.

# Arguments

  * `initial_condition`:  Initial condition representing the system's particles.
  * `sound_speed`:        Speed of sound.
  * `smoothing_kernel`:   Smoothing kernel to be used for this system.                       See [Smoothing Kernels](@ref smoothing_kernel).
  * `smoothing_length`:   Smoothing length to be used for this system.                       See [Smoothing Kernels](@ref smoothing_kernel).

# Keyword Arguments

  * `viscosity`:                  Viscosity model for this system (default: no viscosity).                               Recommended: [`ViscosityAdami`](@ref).
  * `acceleration`:               Acceleration vector for the system. (default: zero vector)
  * `pressure_acceleration`:      Pressure acceleration formulation (default: inter-particle averaged pressure).                               When set to `nothing`, the pressure acceleration formulation for the                               corresponding [density calculator](@ref density_calculator) is chosen.
  * `density_calculator`:         [Density calculator](@ref density_calculator) (default: [`SummationDensity`](@ref))
  * `transport_velocity`:         [Transport Velocity Formulation (TVF)](@ref transport_velocity_formulation). Default is no TVF.
  * `buffer_size`:                Number of buffer particles.                               This is needed when simulating with [`OpenBoundarySPHSystem`](@ref).
  * `correction`:                 Correction method used for this system. (default: no correction, see [Corrections](@ref corrections))
  * `source_terms`:               Additional source terms for this system. Has to be either `nothing`                               (by default), or a function of `(coords, velocity, density, pressure, t)`                               (which are the quantities of a single particle), returning a `Tuple`                               or `SVector` that is to be added to the acceleration of that particle.                               See, for example, [`SourceTermDamping`](@ref).                               Note that these source terms will not be used in the calculation of the                               boundary pressure when using a boundary with                               [`BoundaryModelDummyParticles`](@ref) and [`AdamiPressureExtrapolation`](@ref).                               The keyword argument `acceleration` should be used instead for                               gravity-like source terms.
  * `surface_tension`:            Surface tension model used for this SPH system. (default: no surface tension)
  * `surface_normal_method`:      The surface normal method to be used for this SPH system.                               (default: no surface normal method or `ColorfieldSurfaceNormal()` if a surface_tension model is used)
  * `reference_particle_spacing`: The reference particle spacing used for weighting values at the boundary,                               which currently is only needed when using surface tension.
  * `color_value`:                The value used to initialize the color of particles in the system.
