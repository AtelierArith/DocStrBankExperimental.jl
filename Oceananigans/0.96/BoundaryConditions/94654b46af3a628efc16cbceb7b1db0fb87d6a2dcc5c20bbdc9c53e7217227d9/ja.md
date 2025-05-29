```
FieldBoundaryConditions(; kwargs...)
```

予測フィールドの境界条件のテンプレートを返します。

# キーワード引数

キーワード引数は、7つの可能な境界に対する境界条件を指定します：

  * `west`: `i = 1` のときの `x` 方向の左端点
  * `east`: `i = grid.Nx` のときの `x` 方向の右端点
  * `south`: `j = 1` のときの `y` 方向の左端点
  * `north`: `j = grid.Ny` のときの `y` 方向の右端点
  * `bottom`: `k = 1` のときの `z` 方向の右端点
  * `top`: `k = grid.Nz` のときの `z` 方向の右端点
  * `immersed`: 浸漬境界のための固体と流体の境界

境界条件が指定されていない場合、予測フィールドおよび境界法線方向のトポロジーに対するデフォルトが使用されます：

  * `PeriodicBoundaryCondition` は `Periodic` 方向に対して
  * `NoFluxBoundaryCondition` は `Bounded` 方向および `Centered` に位置するフィールドに対して
  * `ImpenetrableBoundaryCondition` は `Bounded` 方向および `Face` に位置するフィールドに対して
  * `nothing` は `Flat` 方向および/または `Nothing` に位置するフィールドに対して
