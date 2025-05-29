```
Field{LX, LY, LZ}(grid::AbstractGrid,
                  T::DataType=eltype(grid); kw...) where {LX, LY, LZ}

`grid`上に位置`(LX, LY, LZ)`でデータ型`T`の`Field`を構築します。`(LX, LY, LZ)`の各要素は`Center`または`Face`のいずれかであり、それぞれ`(x, y, z)`におけるフィールドの位置を決定します。

# キーワード引数

  * `data :: OffsetArray`: フィールドデータを持つオフセット配列。何も提供されない場合、フィールドはゼロで埋められます。
  * `boundary_conditions`: 何も提供されない場合、[`FieldBoundaryConditions`](@ref)を介してデフォルトの境界条件を使用してフィールドが作成されます。
  * `indices`: 縮小フィールドがどこに存在するかを指定するために使用されます。たとえば、2次元の$x$-$y$フィールドがどの`k`インデックスに存在するかです。デフォルト: `(:, :, :)`。

# 例

位置`(Face, Face, Center)`のフィールド。

```

jldoctest fields julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 3, 4), extent=(1, 1, 1));

julia> ω = Field{Face, Face, Center}(grid) 2×3×4 Field{Face, Face, Center} on RectilinearGrid on CPU ├── grid: 2×3×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo ├── boundary conditions: FieldBoundaryConditions │   └── west: Periodic, east: Periodic, south: Periodic, north: Periodic, bottom: ZeroFlux, top: ZeroFlux, immersed: ZeroFlux └── data: 6×9×10 OffsetArray(::Array{Float64, 3}, -1:4, -2:6, -2:7) with eltype Float64 with indices -1:4×-2:6×-2:7     └── max=0.0, min=0.0, mean=0.0

```

次に、`indices`を使用して、流体の表面$z = 0$での垂直渦度$∂v/∂x - ∂u/∂y$を計算するために、位置`(Face, Face, Center)`の2次元$x$-$y$フィールドを作成できます。`Center`に対応するのは`k = Nz`です。

```

jldoctest fields julia> u = XFaceField(grid); v = YFaceField(grid);

julia> ωₛ = Field(∂x(v) - ∂y(u), indices=(:, :, grid.Nz)) 2×3×1 Field{Face, Face, Center} on RectilinearGrid on CPU ├── grid: 2×3×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo ├── boundary conditions: FieldBoundaryConditions │   └── west: Periodic, east: Periodic, south: Periodic, north: Periodic, bottom: Nothing, top: Nothing, immersed: ZeroFlux ├── indices: (:, :, 4:4) ├── operand: BinaryOperation at (Face, Face, Center) ├── status: time=0.0 └── data: 6×9×1 OffsetArray(::Array{Float64, 3}, -1:4, -2:6, 4:4) with eltype Float64 with indices -1:4×-2:6×4:4     └── max=0.0, min=0.0, mean=0.0

julia> compute!(ωₛ) 2×3×1 Field{Face, Face, Center} on RectilinearGrid on CPU ├── grid: 2×3×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo ├── boundary conditions: FieldBoundaryConditions │   └── west: Periodic, east: Periodic, south: Periodic, north: Periodic, bottom: Nothing, top: Nothing, immersed: ZeroFlux ├── indices: (:, :, 4:4) ├── operand: BinaryOperation at (Face, Face, Center) ├── status: time=0.0 └── data: 6×9×1 OffsetArray(::Array{Float64, 3}, -1:4, -2:6, 4:4) with eltype Float64 with indices -1:4×-2:6×4:4     └── max=0.0, min=0.0, mean=0.0 ```
