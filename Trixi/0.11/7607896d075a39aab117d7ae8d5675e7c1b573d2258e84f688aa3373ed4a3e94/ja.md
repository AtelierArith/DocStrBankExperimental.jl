```
source_terms_convergence_test(u, x, t, equations::CompressibleEulerEquationsQuasi1D)
```

収束テストに使用されるソース項は、[`initial_condition_convergence_test`](@ref)（および非周期的領域における[`BoundaryConditionDirichlet(initial_condition_convergence_test)`](@ref)）と組み合わせて使用されます。

この製造された解のソース項は、[`initial_condition_convergence_test`](@ref)で定義されたモズル幅 'a(x) = 1.5 - 0.5 * cos(x[1] * pi)' のために特別に設計されています。
