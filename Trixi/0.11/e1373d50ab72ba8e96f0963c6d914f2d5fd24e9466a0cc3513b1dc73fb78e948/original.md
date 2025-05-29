```
boundary_condition_poisson_nonperiodic(u_inner, orientation, direction, x, t,
                                       surface_flux_function,
                                       equations::HyperbolicDiffusionEquations1D)
```

Boundary conditions used for convergence tests in combination with [`initial_condition_poisson_nonperiodic`](@ref) and [`source_terms_poisson_nonperiodic`](@ref).
