```
set!(model::HydrostaticFreeSurfaceModel; kwargs...)
```

Set velocity and tracer fields of `model`. The keyword arguments `kwargs...` take the form `name = data`, where `name` refers to one of the fields of either: (i) `model.velocities`, (ii) `model.tracers`, or (iii) `model.free_surface.η`, and the `data` may be an array, a function with arguments `(x, y, z)`, or any data type for which a `set!(ϕ::AbstractField, data)` function exists.

# Example

```jldoctest
using Oceananigans
grid = RectilinearGrid(size=(16, 16, 16), extent=(1, 1, 1))
model = HydrostaticFreeSurfaceModel(; grid, tracers=:T)

# Set u to a parabolic function of z, v to random numbers damped
# at top and bottom, and T to some silly array of half zeros,
# half random numbers.

u₀(x, y, z) = z / model.grid.Lz * (1 + z / model.grid.Lz)
v₀(x, y, z) = 1e-3 * rand() * u₀(x, y, z)

T₀ = rand(size(model.grid)...)
T₀[T₀ .< 0.5] .= 0

set!(model, u=u₀, v=v₀, T=T₀)

model.velocities.u

# output

16×16×16 Field{Face, Center, Center} on RectilinearGrid on CPU
├── grid: 16×16×16 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo
├── boundary conditions: FieldBoundaryConditions
│   └── west: Periodic, east: Periodic, south: Periodic, north: Periodic, bottom: ZeroFlux, top: ZeroFlux, immersed: ZeroFlux
└── data: 22×22×22 OffsetArray(::Array{Float64, 3}, -2:19, -2:19, -2:19) with eltype Float64 with indices -2:19×-2:19×-2:19
    └── max=-0.0302734, min=-0.249023, mean=-0.166992
```
