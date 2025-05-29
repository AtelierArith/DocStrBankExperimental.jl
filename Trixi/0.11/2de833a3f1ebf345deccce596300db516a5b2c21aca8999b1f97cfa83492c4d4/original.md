```
SubcellLimiterIDP(equations::AbstractEquations, basis;
                  local_twosided_variables_cons = String[],
                  positivity_variables_cons = String[],
                  positivity_variables_nonlinear = [],
                  positivity_correction_factor = 0.1,
                  local_onesided_variables_nonlinear = [],
                  max_iterations_newton = 10,
                  newton_tolerances = (1.0e-12, 1.0e-14),
                  gamma_constant_newton = 2 * ndims(equations))
```

Subcell invariant domain preserving (IDP) limiting used with [`VolumeIntegralSubcellLimiting`](@ref) including:

  * Local two-sided Zalesak-type limiting for conservative variables (`local_twosided_variables_cons`)
  * Positivity limiting for conservative variables (`positivity_variables_cons`) and nonlinear variables

(`positivity_variables_nonlinear`)

  * Local one-sided limiting for nonlinear variables, e.g. `entropy_guermond_etal` and `entropy_math`

with `local_onesided_variables_nonlinear`

To use these three limiting options use the following structure:

***Conservative variables*** to be limited are passed as a vector of strings, e.g. `local_twosided_variables_cons = ["rho"]` and `positivity_variables_cons = ["rho"]`. For ***nonlinear variables***, the wanted variable functions are passed within a vector: To ensure positivity use a plain vector including the desired variables, e.g. `positivity_variables_nonlinear = [pressure]`. For local one-sided limiting pass the variable function combined with the requested bound (`min` or `max`) as a tuple. For instance, to impose a lower local bound on the modified specific entropy by Guermond et al. use `local_onesided_variables_nonlinear = [(Trixi.entropy_guermond_etal, min)]`.

The bounds are calculated using the low-order FV solution. The positivity limiter uses `positivity_correction_factor` such that `u^new >= positivity_correction_factor * u^FV`. Local and global limiting of nonlinear variables uses a Newton-bisection method with a maximum of `max_iterations_newton` iterations, relative and absolute tolerances of `newton_tolerances` and a provisional update constant `gamma_constant_newton` (`gamma_constant_newton>=2*d`, where `d = #dimensions`). See equation (20) of Pazner (2020) and equation (30) of Rueda-Ramírez et al. (2022).

!!! note
    This limiter and the correction callback [`SubcellLimiterIDPCorrection`](@ref) only work together. Without the callback, no correction takes place, leading to a standard low-order FV scheme.


## References

  * Rueda-Ramírez, Pazner, Gassner (2022) Subcell Limiting Strategies for Discontinuous Galerkin Spectral Element Methods [DOI: 10.1016/j.compfluid.2022.105627](https://doi.org/10.1016/j.compfluid.2022.105627)
  * Pazner (2020) Sparse invariant domain preserving discontinuous Galerkin methods with subcell convex limiting [DOI: 10.1016/j.cma.2021.113876](https://doi.org/10.1016/j.cma.2021.113876)
