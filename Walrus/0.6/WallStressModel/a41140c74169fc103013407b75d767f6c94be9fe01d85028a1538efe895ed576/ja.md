```
WallStress(; von_Karman_constant = 0.4,
             kinematic_viscosity = 1e-6,
             B = 5.2,
             precomputed_friction_velocities = false,
             precompute_speeds = [0:25/100000:25;],
             grid = nothing,
             arch = isnothing(grid) ? CPU() : architecture(grid))
```

これは、[SCHUMANN1975376](@citet)、[HARTEL1996283](@citet)、[Piomelli1989](@citet)、および[taylor2007](@citet)で提案されたものに類似したデフォルトパラメータを持つLESシミュレーション用の壁応力モデルを返します。

摩擦速度は、`precomputed_friction_velocities`がtrueであり、`grid`が提供されている場合に`precompute_speeds`で事前に計算されます。

# キーワード引数

  * `von_Karman_constant`: von Karman壁応力定数
  * `kinematic_viscosity`: 壁の上の水の運動粘度
  * `B`: 壁応力定数
  * `precomputed_friction_velocities`: 摩擦速度を事前に計算しますか？
  * `precompute_speeds`: 摩擦速度を事前に計算するための底水速度、これはシミュレーションで可能な速度範囲を含む必要があります
  * `grid`: 摩擦速度を事前に計算するためのグリッド
  * `arch`: 事前に計算された摩擦速度に適応するアーキテクチャ

# 例

```jldoctest
julia> using Walrus: WallStress

julia> using Oceananigans

julia> wall_stress = WallStress()
(::WallStress{Float64, Nothing}) (generic function with 1 method)
julia> boundary_conditions = (u = FieldBoundaryConditions(bottom = FluxBoundaryCondition(wall_stress, discrete_form = true, parameters = Val(:x))),
                              v = FieldBoundaryConditions(bottom = FluxBoundaryCondition(wall_stress, discrete_form = true, parameters = Val(:y))))
(u = Oceananigans.FieldBoundaryConditions, with boundary conditions
├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── bottom: FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:x}
├── top: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
└── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing), v = Oceananigans.FieldBoundaryConditions, with boundary conditions
├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── bottom: FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:y}
├── top: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
└── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing))

```
