```
WENO([FT=Float64, FT2=Float32;]
     order = 5,
     grid = nothing,
     bounds = nothing)

# 引数

  * `FT`: スキームで使用される浮動小数点型。デフォルト: `Oceananigans.defaults.FloatType`
  * `FT2`: スキームの一部のパフォーマンスクリティカルな部分で使用される浮動小数点型。デフォルト: `Float32`

# キーワード引数

  * `order`: WENO移流スキームの次数。デフォルト: 5
  * `grid`: (デフォルトは`nothing`)

# 例

```

jldoctest julia> using Oceananigans

julia> WENO() WENO(order=5)  Boundary scheme:     └── WENO(order=3)  Symmetric scheme:     └── Centered(order=4)

```

```

jldoctest julia> using Oceananigans

julia> Nx, Nz = 16, 10;

julia> Lx, Lz = 1e4, 1e3;

julia> chebychev*spaced*z_faces(k) = - Lz/2 - Lz/2 * cos(π * (k - 1) / Nz);

julia> grid = RectilinearGrid(size = (Nx, Nz), halo = (4, 4), topology=(Periodic, Flat, Bounded),                               x = (0, Lx), z = chebychev*spaced*z_faces);

julia> WENO(grid; order=7) WENO(order=7)  Boundary scheme:     └── WENO(order=5)  Symmetric scheme:     └── Centered(order=6) ```
