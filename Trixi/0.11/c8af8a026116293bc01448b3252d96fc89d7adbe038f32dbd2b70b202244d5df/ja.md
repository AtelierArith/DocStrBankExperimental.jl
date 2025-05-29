```
source_terms_convergence_test(u, x, t, equations::ShallowWaterEquationsQuasi1D)
```

収束テストに使用されるソース項は、[`initial_condition_convergence_test`](@ref)（および非周期的領域における[`BoundaryConditionDirichlet(initial_condition_convergence_test)`](@ref)）と組み合わせて使用されます。

この製造された解のソース項は、特に底面地形関数 `b(x) = 0.2 - 0.05 * sinpi(sqrt(2) * x[1])` と、[`initial_condition_convergence_test`](@ref)で定義されたチャネル幅 'a(x)= 1 + 0.1 * cospi(sqrt(2) * x[1])' のために特別に設計されています。
