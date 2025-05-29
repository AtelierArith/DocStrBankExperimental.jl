```
source_terms_convergence_test(u, x, t, equations::ShallowWaterEquations2D)
```

Source terms used for convergence tests in combination with [`initial_condition_convergence_test`](@ref) (and [`BoundaryConditionDirichlet(initial_condition_convergence_test)`](@ref) in non-periodic domains).

This manufactured solution source term is specifically designed for the bottom topography function `b(x,y) = 2 + 0.5 * sinpi(sqrt(2) * x) + 0.5 * sinpi(sqrt(2) * y)` as defined in [`initial_condition_convergence_test`](@ref).
