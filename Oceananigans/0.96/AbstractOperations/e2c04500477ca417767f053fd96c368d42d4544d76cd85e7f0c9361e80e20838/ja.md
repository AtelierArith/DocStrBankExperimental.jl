```
xspacings(grid, ℓx, ℓy, ℓz)
```

`grid` の位置 `ℓx, ℓy, ℓz` における $x$ 方向のグリッド間隔を計算する `KernelFunctionOperation` を返します。

# 例

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> xspacings(grid, Center(), Center(), Center())
KernelFunctionOperation at (Center, Center, Center)
├── grid: 2×4×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo
├── kernel_function: Δx (generic function with 29 methods)
└── arguments: ("Center", "Center", "Center")
```
