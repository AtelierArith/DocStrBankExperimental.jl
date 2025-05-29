```
struct Isothermal
```

[`BoundaryConditionNavierStokesWall`](@ref)を使用して、滑らない境界条件を作成するために使用されます。フィールド`boundary_value_function`は、シグネチャ`boundary_value_function(x, t, equations)`を持つ関数である必要があり、点`x`と時間`t`における温度のスカラー値を返す必要があります。
