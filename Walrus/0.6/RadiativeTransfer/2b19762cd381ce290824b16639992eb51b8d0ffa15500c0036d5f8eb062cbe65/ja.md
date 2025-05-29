```
HomogeneousBodyHeating(; surface_flux,
                         water_attenuation_coefficient = 1.8,
                         water_heat_capacity = 3991.0, # J K⁻¹ kg⁻¹
                         water_density = 1026.0) # kg m⁻³
```

`surface_flux` (W / m²) によって水が減衰し、加熱されるモデルを作成します。これは Oceananigans と相互作用し、ボディ強制として機能します。

# キーワード引数

  * `surface_flux` (必須): `surface_flux(x, y, t)` の形式で表面放射フラックスを返す関数または単一の値
  * `water_attenuation_coefficient`: 水の放射減衰係数
  * `water_heat_capacity`: 水の比熱容量
  * `water_density`: 水の密度

# 例

```jldoctest; filter = r".*@ Walrus.RadiativeTransfer.*"
julia> using Walrus: HomogeneousBodyHeating

julia> using Oceananigans

julia> grid = RectilinearGrid(size = (128, 128, 128), extent = (1000, 1000, 1000))
128×128×128 RectilinearGrid{Float64, Oceananigans.Grids.Periodic, Oceananigans.Grids.Periodic, Oceananigans.Grids.Bounded} on Oceananigans.Architectures.CPU with 3×3×3 halo
├── Periodic x ∈ [0.0, 1000.0)  regularly spaced with Δx=7.8125
├── Periodic y ∈ [0.0, 1000.0)  regularly spaced with Δy=7.8125
└── Bounded  z ∈ [-1000.0, 0.0] regularly spaced with Δz=7.8125
julia> body_heating = HomogeneousBodyHeating(; surface_flux = (x, y, t) -> 100)
(::HomogeneousBodyHeating{Float64, Walrus.ContinuousSurfaceFunction{var"#1#2"}}) (generic function with 1 method)

julia> model = NonhydrostaticModel(; grid, forcing = (; T = Forcing(body_heating, discrete_form=true)), tracers = :T)
NonhydrostaticModel{CPU, RectilinearGrid}(time = 0 seconds, iteration = 0)
├── grid: 128×128×128 RectilinearGrid{Float64, Oceananigans.Grids.Periodic, Oceananigans.Grids.Periodic, Oceananigans.Grids.Bounded} on Oceananigans.Architectures.CPU with 3×3×3 halo
├── timestepper: RungeKutta3TimeStepper
├── advection scheme: Centered(order=2)
├── tracers: T
├── closure: Nothing
├── buoyancy: Nothing
└── coriolis: Nothing
```
