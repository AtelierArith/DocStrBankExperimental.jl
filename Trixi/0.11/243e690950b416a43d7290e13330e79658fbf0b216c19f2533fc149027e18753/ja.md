```
struct NoSlip
```

[`BoundaryConditionNavierStokesWall`](@ref)を使用して、スリップのない境界条件を作成します。フィールド`boundary_value_function`は、シグネチャ`boundary_value_function(x, t, equations)`を持つ関数である必要があり、`SVector{NDIMS}`を返す必要があります。そのエントリは、点`x`と時間`t`での速度ベクトルです。
