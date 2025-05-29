```
Field{LX, LY, LZ}(grid::AbstractGrid,
                  T::DataType=eltype(grid); kw...) where {LX, LY, LZ}
```

Construct a `Field` on `grid` with data type `T` at the location `(LX, LY, LZ)`. Each of `(LX, LY, LZ)` is either `Center` or `Face` and determines the field's location in `(x, y, z)` respectively.

# Keyword arguments

  * `data :: OffsetArray`: An offset array with the fields data. If nothing is provided the field is filled with zeros.
  * `boundary_conditions`: If nothing is provided, then field is created using the default boundary conditions via [`FieldBoundaryConditions`](@ref).
  * `indices`: Used to prescribe where a reduced field lives on. For example, at which `k` index does a two-dimensional $x$-$y$ field lives on. Default: `(:, :, :)`.

# Example

A field at location `(Face, Face, Center)`.

```jldoctest fields
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 3, 4), extent=(1, 1, 1));

julia> ω = Field{Face, Face, Center}(grid)
2×3×4 Field{Face, Face, Center} on RectilinearGrid on CPU
├── grid: 2×3×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo
├── boundary conditions: FieldBoundaryConditions
│   └── west: Periodic, east: Periodic, south: Periodic, north: Periodic, bottom: ZeroFlux, top: ZeroFlux, immersed: ZeroFlux
└── data: 6×9×10 OffsetArray(::Array{Float64, 3}, -1:4, -2:6, -2:7) with eltype Float64 with indices -1:4×-2:6×-2:7
    └── max=0.0, min=0.0, mean=0.0
```

Now, using `indices` we can create a two dimensional $x$-$y$ field at location `(Face, Face, Center)` to compute, e.g., the vertical vorticity $∂v/∂x - ∂u/∂y$ at the fluid's surface $z = 0$, which for `Center` corresponds to `k = Nz`.

```jldoctest fields
julia> u = XFaceField(grid); v = YFaceField(grid);

julia> ωₛ = Field(∂x(v) - ∂y(u), indices=(:, :, grid.Nz))
2×3×1 Field{Face, Face, Center} on RectilinearGrid on CPU
├── grid: 2×3×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo
├── boundary conditions: FieldBoundaryConditions
│   └── west: Periodic, east: Periodic, south: Periodic, north: Periodic, bottom: Nothing, top: Nothing, immersed: ZeroFlux
├── indices: (:, :, 4:4)
├── operand: BinaryOperation at (Face, Face, Center)
├── status: time=0.0
└── data: 6×9×1 OffsetArray(::Array{Float64, 3}, -1:4, -2:6, 4:4) with eltype Float64 with indices -1:4×-2:6×4:4
    └── max=0.0, min=0.0, mean=0.0

julia> compute!(ωₛ)
2×3×1 Field{Face, Face, Center} on RectilinearGrid on CPU
├── grid: 2×3×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo
├── boundary conditions: FieldBoundaryConditions
│   └── west: Periodic, east: Periodic, south: Periodic, north: Periodic, bottom: Nothing, top: Nothing, immersed: ZeroFlux
├── indices: (:, :, 4:4)
├── operand: BinaryOperation at (Face, Face, Center)
├── status: time=0.0
└── data: 6×9×1 OffsetArray(::Array{Float64, 3}, -1:4, -2:6, 4:4) with eltype Float64 with indices -1:4×-2:6×4:4
    └── max=0.0, min=0.0, mean=0.0
```
