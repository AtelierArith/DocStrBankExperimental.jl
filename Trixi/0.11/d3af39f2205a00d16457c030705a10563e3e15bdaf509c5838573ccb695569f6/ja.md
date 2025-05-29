```
source_terms_poisson_nonperiodic(u, x, t,
                                 equations::HyperbolicDiffusionEquations1D)
```

強制関数 `f(x)` を含むソース項と、[`initial_condition_poisson_nonperiodic`](@ref) および [`boundary_condition_poisson_nonperiodic`](@ref) と共に使用されるハイパーボリック拡散システムの右辺。
