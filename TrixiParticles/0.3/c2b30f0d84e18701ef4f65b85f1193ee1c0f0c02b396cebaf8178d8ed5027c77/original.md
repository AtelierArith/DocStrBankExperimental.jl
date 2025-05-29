```
WeaklyCompressibleSPHSystem(initial_condition,
                            density_calculator, state_equation,
                            smoothing_kernel, smoothing_length;
                            viscosity=nothing, density_diffusion=nothing,
                            transport_velocity=nothing,
                            acceleration=ntuple(_ -> 0.0, NDIMS),
                            buffer_size=nothing,
                            correction=nothing, source_terms=nothing,
                            surface_tension=nothing, surface_normal_method=nothing,
                            reference_particle_spacing=0.0))
```

System for particles of a fluid. The weakly compressible SPH (WCSPH) scheme is used, wherein a stiff equation of state generates large pressure changes for small density variations. See [Weakly Compressible SPH](@ref wcsph) for more details on the method.

# Arguments

  * `initial_condition`:  [`InitialCondition`](@ref) representing the system's particles.
  * `density_calculator`: Density calculator for the system.                       See [`ContinuityDensity`](@ref) and [`SummationDensity`](@ref).
  * `state_equation`:     Equation of state for the system. See [`StateEquationCole`](@ref).
  * `smoothing_kernel`:   Smoothing kernel to be used for this system.                       See [Smoothing Kernels](@ref smoothing_kernel).
  * `smoothing_length`:   Smoothing length to be used for this system.                       See [Smoothing Kernels](@ref smoothing_kernel).

# Keyword Arguments

  * `viscosity`:                  Viscosity model for this system (default: no viscosity).                               See [`ArtificialViscosityMonaghan`](@ref) or [`ViscosityAdami`](@ref).
  * `transport_velocity`:         [Transport Velocity Formulation (TVF)](@ref transport_velocity_formulation). Default is no TVF.
  * `density_diffusion`:          Density diffusion terms for this system. See [`DensityDiffusion`](@ref).
  * `acceleration`:               Acceleration vector for the system. (default: zero vector)
  * `buffer_size`:                Number of buffer particles.                               This is needed when simulating with [`OpenBoundarySPHSystem`](@ref).
  * `correction`:                 Correction method used for this system. (default: no correction, see [Corrections](@ref corrections))
  * `source_terms`:               Additional source terms for this system. Has to be either `nothing`                               (by default), or a function of `(coords, velocity, density, pressure, t)`                               (which are the quantities of a single particle), returning a `Tuple`                               or `SVector` that is to be added to the acceleration of that particle.                               See, for example, [`SourceTermDamping`](@ref).                               Note that these source terms will not be used in the calculation of the                               boundary pressure when using a boundary with                               [`BoundaryModelDummyParticles`](@ref) and [`AdamiPressureExtrapolation`](@ref).                               The keyword argument `acceleration` should be used instead for                               gravity-like source terms.
  * `surface_tension`:            Surface tension model used for this SPH system. (default: no surface tension)
  * `surface_normal_method`:      The surface normal method to be used for this SPH system.                               (default: no surface normal method or `ColorfieldSurfaceNormal()` if a surface_tension model is used)
  * `reference_particle_spacing`: The reference particle spacing used for weighting values at the boundary,                               which currently is only needed when using surface tension.
  * `color_value`:                The value used to initialize the color of particles in the system.
