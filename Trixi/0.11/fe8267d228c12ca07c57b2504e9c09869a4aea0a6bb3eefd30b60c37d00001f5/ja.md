```
initial_condition_convergence_test(x, t, equations::CompressibleEulerEquationsQuasi1D)
```

収束テストに使用される滑らかな初期条件で、[`source_terms_convergence_test`](@ref)（および非周期領域での[`BoundaryConditionDirichlet(initial_condition_convergence_test)`](@ref）と組み合わせて使用されます）。
