```
TotalLagrangianSPHSystem(initial_condition,
                         smoothing_kernel, smoothing_length,
                         young_modulus, poisson_ratio;
                         n_fixed_particles=0, boundary_model=nothing,
                         acceleration=ntuple(_ -> 0.0, NDIMS),
                         penalty_force=nothing, source_terms=nothing)
```

System for particles of an elastic structure.

A Total Lagrangian framework is used wherein the governing equations are formulated such that all relevant quantities and operators are measured with respect to the initial configuration (O’Connor & Rogers 2021, Belytschko et al. 2000). See [Total Lagrangian SPH](@ref tlsph) for more details on the method.

# Arguments

  * `initial_condition`:  Initial condition representing the system's particles.
  * `young_modulus`:      Young's modulus.
  * `poisson_ratio`:      Poisson ratio.
  * `smoothing_kernel`:   Smoothing kernel to be used for this system.                       See [Smoothing Kernels](@ref smoothing_kernel).
  * `smoothing_length`:   Smoothing length to be used for this system.                       See [Smoothing Kernels](@ref smoothing_kernel).

# Keyword Arguments

  * `n_fixed_particles`:  Number of fixed particles which are used to clamp the structure                       particles. Note that the fixed particles must be the **last**                       particles in the `InitialCondition`. See the info box below.
  * `boundary_model`: Boundary model to compute the hydrodynamic density and pressure for                   fluid-structure interaction (see [Boundary Models](@ref boundary_models)).
  * `penalty_force`:  Penalty force to ensure regular particle position under large deformations                   (see [`PenaltyForceGanzenmueller`](@ref)).
  * `acceleration`:   Acceleration vector for the system. (default: zero vector)
  * `source_terms`:   Additional source terms for this system. Has to be either `nothing`                   (by default), or a function of `(coords, velocity, density, pressure)`                   (which are the quantities of a single particle), returning a `Tuple`                   or `SVector` that is to be added to the acceleration of that particle.                   See, for example, [`SourceTermDamping`](@ref).

!!! note
    The fixed particles must be the **last** particles in the `InitialCondition`. To do so, e.g. use the `union` function:

    ```jldoctest; output = false, setup = :(fixed_particles = RectangularShape(0.1, (1, 4), (0.0, 0.0), density=1.0); beam = RectangularShape(0.1, (3, 4), (0.1, 0.0), density=1.0))
    solid = union(beam, fixed_particles)

    # output
    ┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
    │ InitialCondition{Float64}                                                                        │
    │ ═════════════════════════                                                                        │
    │ #dimensions: ……………………………………………… 2                                                                │
    │ #particles: ………………………………………………… 16                                                               │
    │ particle spacing: ………………………………… 0.1                                                              │
    └──────────────────────────────────────────────────────────────────────────────────────────────────┘
    ```

    where `beam` and `fixed_particles` are of type `InitialCondition`.

