```
source_terms_convergence_test(u, x, t, equations::ShallowWaterEquations1D)
```

Source terms used for convergence tests in combination with [`initial_condition_convergence_test`](@ref) (and [`BoundaryConditionDirichlet(initial_condition_convergence_test)`](@ref) in non-periodic domains).

This manufactured solution source term is specifically designed for the bottom topography function `b(x) = 2.0 + 0.5 * sinpi(sqrt(2.0) * x[1])` as defined in [`initial_condition_convergence_test`](@ref).
