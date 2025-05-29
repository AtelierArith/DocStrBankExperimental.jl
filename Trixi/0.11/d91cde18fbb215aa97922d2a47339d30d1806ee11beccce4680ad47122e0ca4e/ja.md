```
source_terms_convergence_test(u, x, t, equations::CompressibleEulerEquations1D)
```

収束テストに使用されるソース項で、[`initial_condition_convergence_test`](@ref)（および非周期領域における[`BoundaryConditionDirichlet(initial_condition_convergence_test)`](@ref)）と組み合わせて使用されます。
