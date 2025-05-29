```
source_terms_convergence_test(u, x, t, equations::ShallowWaterEquations2D)
```

収束テストに使用されるソース項は、[`initial_condition_convergence_test`](@ref)（および非周期的領域における[`BoundaryConditionDirichlet(initial_condition_convergence_test)`](@ref)）と組み合わせて使用されます。

この製造された解のソース項は、[`initial_condition_convergence_test`](@ref)で定義された底面地形関数 `b(x,y) = 2 + 0.5 * sinpi(sqrt(2) * x) + 0.5 * sinpi(sqrt(2) * y)` のために特別に設計されています。
