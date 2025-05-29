```
source_terms_poisson_nonperiodic(u, x, t,
                                 equations::HyperbolicDiffusionEquations1D)
```

Source terms that include the forcing function `f(x)` and right hand side for the hyperbolic diffusion system that is used with [`initial_condition_poisson_nonperiodic`](@ref) and [`boundary_condition_poisson_nonperiodic`](@ref).
