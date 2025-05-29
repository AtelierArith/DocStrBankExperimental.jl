```
minimum_yspacing(grid, ℓx, ℓy, ℓz)
```

`grid`の位置`ℓx, ℓy, ℓz`における$y$方向の最小間隔を返します。

# 例

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> minimum_yspacing(grid, Center(), Center(), Center())
0.25
```
