```
WallStressBoundaryConditions(; von_Karman_constant = 0.4,
                               kinematic_viscosity = 1e-6,
                               B = 5.2,
                               precompute_speeds = [0:25/100000:25;],
                               grid = nothing)

`WallStress`境界条件を設定するための便利なコンストラクタ。

# キーワード引数

  * `von_Karman_constant`: von Karman壁応力定数
  * `kinematic_viscosity`: 壁の上の水の運動粘度
  * `B`: 壁応力定数
  * `precomputed_friction_velocities`: 摩擦速度を事前計算しますか？
  * `precompute_speeds`: 摩擦速度を事前計算するための底水速度、これはシミュレーションで可能な速度の範囲を含む必要があります
  * `grid`: 摩擦速度を事前計算するためのグリッド

# 例

```

jldoctest julia> using Walrus: WallStressBoundaryConditions

julia> using Oceananigans

julia> stress*boundary*conditions = WallStressBoundaryConditions() (u = FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:x}, v = FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:y}) julia> boundary*conditions = (u = FieldBoundaryConditions(bottom = stress*boundary*conditions.u),                               v = FieldBoundaryConditions(bottom = stress*boundary_conditions.v)) (u = Oceananigans.FieldBoundaryConditions, with boundary conditions ├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) ├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) ├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) ├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) ├── bottom: FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:x} ├── top: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) └── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing), v = Oceananigans.FieldBoundaryConditions, with boundary conditions ├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) ├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) ├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) ├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) ├── bottom: FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:y} ├── top: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing) └── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)) ```
