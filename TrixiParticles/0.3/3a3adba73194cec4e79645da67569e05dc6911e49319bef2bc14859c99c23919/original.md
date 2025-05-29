```
BoundaryModelDummyParticles(initial_density, hydrodynamic_mass,
                            density_calculator, smoothing_kernel,
                            smoothing_length; viscosity=nothing,
                            state_equation=nothing, correction=nothing,
                            reference_particle_spacing=0.0)
```

Boundary model for `BoundarySPHSystem`.

# Arguments

  * `initial_density`: Vector holding the initial density of each boundary particle.
  * `hydrodynamic_mass`: Vector holding the "hydrodynamic mass" of each boundary particle.                      See description above for more information.
  * `density_calculator`: Strategy to compute the hydrodynamic density of the boundary particles.                       See description below for more information.
  * `smoothing_kernel`: Smoothing kernel should be the same as for the adjacent fluid system.
  * `smoothing_length`: Smoothing length should be the same as for the adjacent fluid system.

# Keywords

  * `state_equation`:             This should be the same as for the adjacent fluid system                               (see e.g. [`StateEquationCole`](@ref)).
  * `correction`:                 Correction method of the adjacent fluid system (see [Corrections](@ref corrections)).
  * `viscosity`:                  Slip (default) or no-slip condition. See description below for further                               information.
  * `reference_particle_spacing`: The reference particle spacing used for weighting values at the boundary,                               which currently is only needed when using surface tension.

# Examples

```jldoctest; output = false, setup = :(densities = [1.0, 2.0, 3.0]; masses = [0.1, 0.2, 0.3]; smoothing_kernel = SchoenbergCubicSplineKernel{2}(); smoothing_length = 0.1)
# Free-slip condition
boundary_model = BoundaryModelDummyParticles(densities, masses, AdamiPressureExtrapolation(),
                                             smoothing_kernel, smoothing_length)

# No-slip condition
boundary_model = BoundaryModelDummyParticles(densities, masses, AdamiPressureExtrapolation(),
                                             smoothing_kernel, smoothing_length,
                                             viscosity=ViscosityAdami(nu=1e-6))

# output
BoundaryModelDummyParticles(AdamiPressureExtrapolation, ViscosityAdami)
```
