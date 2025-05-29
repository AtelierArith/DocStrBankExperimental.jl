```
minimum_zspacing(grid, ℓx, ℓy, ℓz)
minimum_zspacing(grid) = minimum_zspacing(grid, Center(), Center(), Center())
```

`grid`の$z$方向の最小間隔を位置`ℓx, ℓy, ℓz`で返します。

# 例

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> minimum_zspacing(grid, Center(), Center(), Center())
0.125
```
