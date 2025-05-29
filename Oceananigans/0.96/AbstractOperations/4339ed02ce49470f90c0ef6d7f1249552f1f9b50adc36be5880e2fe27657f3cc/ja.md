```
yspacings(grid, ℓx, ℓy, ℓz)
```

`grid`の$y$方向のグリッド間隔を、位置`ℓx, ℓy, ℓz`で計算する`KernelFunctionOperation`を返します。

# 例

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> yspacings(grid, Center(), Face(), Center())
KernelFunctionOperation at (Center, Face, Center)
├── grid: 2×4×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo
├── kernel_function: Δy (generic function with 29 methods)
└── arguments: ("Center", "Face", "Center")
```
