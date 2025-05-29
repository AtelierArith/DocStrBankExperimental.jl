```
BuoyancyForce(formulation; gravity_unit_vector=NegativeZDirection())
```

`model`を用いて`buoyancy`を構築します。オプションのキーワード引数`gravity_unit_vector`を使用して重力の方向を指定できます（デフォルトは`NegativeZDirection()`）。浮力加速度は重力とは反対の方向に作用します。

# 例

```jldoctest
using Oceananigans

grid = RectilinearGrid(size=(1, 8, 8), extent=(1, 1, 1))

θ = 45 # 度
g̃ = (0, -sind(θ), -cosd(θ))

buoyancy = BuoyancyForce(BuoyancyTracer(), gravity_unit_vector=g̃)

model = NonhydrostaticModel(; grid, buoyancy, tracers=:b)

# 出力

NonhydrostaticModel{CPU, RectilinearGrid}(time = 0 seconds, iteration = 0)
├── grid: 1×8×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×3×3 halo
├── timestepper: RungeKutta3TimeStepper
├── advection scheme: Centered(order=2)
├── tracers: b
├── closure: Nothing
├── buoyancy: BuoyancyTracer with ĝ = (0.0, -0.707107, -0.707107)
└── coriolis: Nothing
```
