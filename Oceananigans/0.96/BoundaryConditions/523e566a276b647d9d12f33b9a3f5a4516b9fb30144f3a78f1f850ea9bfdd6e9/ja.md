```
FieldBoundaryConditions(grid, location, indices=(:, :, :);
                        west     = default_auxiliary_bc(grid, boundary, loc),
                        east     = default_auxiliary_bc(grid, boundary, loc),
                        south    = default_auxiliary_bc(grid, boundary, loc), 
                        north    = default_auxiliary_bc(grid, boundary, loc), 
                        bottom   = default_auxiliary_bc(grid, boundary, loc), 
                        top      = default_auxiliary_bc(grid, boundary, loc), 
                        immersed = NoFluxBoundaryCondition())
```

`grid` と `location` における補助フィールド（モデルの予測フィールドから導出された値を持つフィールド）の境界条件を返します。

# キーワード引数

キーワード引数は、6つの可能な境界に対する境界条件を指定します：

  * `west`、`x`方向の左端点で `i = 1`
  * `east`、`x`方向の右端点で `i = grid.Nx`
  * `south`、`y`方向の左端点で `j = 1`
  * `north`、`y`方向の右端点で `j = grid.Ny`
  * `bottom`、`z`方向の右端点で `k = 1`
  * `top`、`z`方向の右端点で `k = grid.Nz`
  * `immersed`：浸漬境界の固体と流体の間の境界

境界条件が指定されていない場合、補助フィールドと境界法線方向のトポロジーに対してデフォルトが使用されます：

  * `PeriodicBoundaryCondition` は `Periodic` 方向に対して
  * `GradientBoundaryCondition(0)` は `Bounded` 方向および `Centered` に位置するフィールドに対して
  * `nothing` は `Bounded` 方向および `Face` に位置するフィールドに対して
  * `nothing` は `Flat` 方向および/または `Nothing` に位置するフィールドに対して
