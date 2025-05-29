```
struct Adiabatic
```

[`BoundaryConditionNavierStokesWall`](@ref)を使用して、滑らない境界条件を作成します。フィールド`boundary_value_normal_flux_function`は、`boundary_value_normal_flux_function(x, t, equations)`というシグネチャを持つ関数であり、点`x`と時間`t`における法線熱フラックスのスカラー値を返す必要があります。
