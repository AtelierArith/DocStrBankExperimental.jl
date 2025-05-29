```
source_terms_convergence_test(u, x, t, equations::CompressibleEulerEquationsQuasi1D)
```

Source terms used for convergence tests in combination with [`initial_condition_convergence_test`](@ref) (and [`BoundaryConditionDirichlet(initial_condition_convergence_test)`](@ref) in non-periodic domains).

This manufactured solution source term is specifically designed for the mozzle width 'a(x) = 1.5 - 0.5 * cos(x[1] * pi)' as defined in [`initial_condition_convergence_test`](@ref).
