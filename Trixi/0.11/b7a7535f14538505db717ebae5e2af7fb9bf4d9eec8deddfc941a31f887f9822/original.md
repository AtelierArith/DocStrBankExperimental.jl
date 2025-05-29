```
ParametersEulerGravity(; background_density=0.0,
                         gravitational_constant=1.0,
                         cfl=1.0,
                         resid_tol=1.0e-4,
                         n_iterations_max=10^4,
                         timestep_gravity=timestep_gravity_erk52_3Sstar!)
```

Set up parameters for the gravitational part of a [`SemidiscretizationEulerGravity`](@ref).

# Arguments

  * `background_density<:Real`: Constant background/reference density ρ₀ which is subtracted from the (Euler) density                             in the RHS source term computation of the gravity solver.
  * `gravitational_constant<:Real`: Gravitational constant G which needs to be in consistent units with the                                 density and velocity fields.
  * `cfl<:Real`: CFL number used for the pseudo-time stepping to advance the hyperbolic diffusion equations into steady state.
  * `resid_tol<:Real`: Absolute tolerance for the residual of the hyperbolic diffusion equations which are solved to                     (approximately) steady state.
  * `n_iterations_max::Int`: Maximum number of iterations of the pseudo-time gravity solver.                           If `n_iterations <= 0` the solver will iterate until the residual is less or equal `resid_tol`.                           This can cause an infinite loop if the solver does not converge!
  * `timestep_gravity`: Function to advance the gravity solver by one pseudo-time step.                     There are three optimized methods available:                      1) `timestep_gravity_erk51_3Sstar!` (first-order),                     2) `timestep_gravity_erk52_3Sstar!` (second-order),                     3) `timestep_gravity_erk53_3Sstar!` (third-order).                     Additionally, `timestep_gravity_carpenter_kennedy_erk54_2N!` (fourth-order) can be used.
