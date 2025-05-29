```
set!(model::HydrostaticFreeSurfaceModel; kwargs...)
```

`model`の速度とトレーサーフィールドを設定します。キーワード引数`kwargs...`は`name = data`の形式を取り、`name`は次のいずれかのフィールドを指します：(i) `model.velocities`、(ii) `model.tracers`、または(iii) `model.free_surface.η`、そして`data`は配列、引数`(x, y, z)`を持つ関数、または`set!(ϕ::AbstractField, data)`関数が存在する任意のデータ型である可能性があります。

# 例

```jldoctest
using Oceananigans
grid = RectilinearGrid(size=(16, 16, 16), extent=(1, 1, 1))
model = HydrostaticFreeSurfaceModel(; grid, tracers=:T)

# uをzの放物線関数に、vを上部と下部で減衰したランダム数に、
# Tを半分がゼロ、半分がランダム数のいくつかのばかげた配列に設定します。

u₀(x, y, z) = z / model.grid.Lz * (1 + z / model.grid.Lz)
v₀(x, y, z) = 1e-3 * rand() * u₀(x, y, z)

T₀ = rand(size(model.grid)...)
T₀[T₀ .< 0.5] .= 0

set!(model, u=u₀, v=v₀, T=T₀)

model.velocities.u

# 出力

16×16×16 Field{Face, Center, Center} on RectilinearGrid on CPU
├── grid: 16×16×16 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo
├── boundary conditions: FieldBoundaryConditions
│   └── west: Periodic, east: Periodic, south: Periodic, north: Periodic, bottom: ZeroFlux, top: ZeroFlux, immersed: ZeroFlux
└── data: 22×22×22 OffsetArray(::Array{Float64, 3}, -2:19, -2:19, -2:19) with eltype Float64 with indices -2:19×-2:19×-2:19
    └── max=-0.0302734, min=-0.249023, mean=-0.166992
```
