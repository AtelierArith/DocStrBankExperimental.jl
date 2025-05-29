```
boundary_condition_poisson_nonperiodic(u_inner, orientation, direction, x, t,
                                       surface_flux_function,
                                       equations::HyperbolicDiffusionEquations1D)
```

収束テストに使用される境界条件で、[`initial_condition_poisson_nonperiodic`](@ref)および[`source_terms_poisson_nonperiodic`](@ref)と組み合わせて使用されます。
