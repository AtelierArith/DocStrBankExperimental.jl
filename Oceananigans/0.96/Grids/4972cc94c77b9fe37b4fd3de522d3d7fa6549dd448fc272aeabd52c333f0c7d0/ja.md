```
minimum_xspacing(grid, ℓx, ℓy, ℓz)
```

`grid`の$x$方向の最小間隔を位置`ℓx, ℓy, ℓz`で返します。

# 例

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> minimum_xspacing(grid, Center(), Center(), Center())
0.5
```
