```
zspacings(grid, ℓx, ℓy, ℓz)
```

`grid`の位置`ℓx, ℓy, ℓz`における$z$方向のグリッド間隔を計算する`KernelFunctionOperation`を返します。

# 例

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> zspacings(grid, Center(), Center(), Face())
KernelFunctionOperation at (Center, Center, Face)
├── grid: 2×4×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo
├── kernel_function: Δz (generic function with 28 methods)
└── arguments: ("Center", "Center", "Face")
```
