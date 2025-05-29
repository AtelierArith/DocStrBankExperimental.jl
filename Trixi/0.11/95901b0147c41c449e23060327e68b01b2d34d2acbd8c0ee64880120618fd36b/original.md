```
initial_condition_poisson_nonperiodic(x, t, equations::HyperbolicDiffusionEquations1D)
```

A non-priodic smooth initial condition. Can be used for convergence tests in combination with [`source_terms_poisson_nonperiodic`](@ref) and [`boundary_condition_poisson_nonperiodic`](@ref).

!!! note
    The solution is periodic but the initial guess is not.

