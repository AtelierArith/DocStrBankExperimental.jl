```
BoundaryConditions([T=Float64;] bottom = GradientBoundaryCondition(-zero(T)),
                                   top = FluxBoundaryCondition(-zero(T)))
```

`FieldBoundaryConditions`を返し、`bottom`と`top`の境界条件を持ちます。型`T`は、`bottom`と`top`のデフォルト値にのみ関連しています。
