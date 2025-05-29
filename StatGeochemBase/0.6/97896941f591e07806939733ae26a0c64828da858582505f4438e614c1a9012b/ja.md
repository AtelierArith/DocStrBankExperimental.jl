```julia
(columns, rows) = find_grid_inpolygon(grid_x, grid_y, poly_x, poly_y)
```

多角形内にあるグリッドポイントのインデックスを見つけます。グリッドのセル中心は grid*x（グリッドの j 列）および grid*y（グリッドの i 行）で与えられます。多角形内の行と列のリストを返します。

### 例

```julia julia> grid_x = -1.5:1/3:1.5;

julia> grid_y = -1.5:1/3:1.5;

julia> cols,rows = find*grid*inpolygon(gridx, gridy, [-.4,.4,.4,-.4],[.4,.4,-.4,-.4]) ([5, 5, 6, 6], [5, 6, 5, 6])

julia> grid_x[cols] 4-element Vector{Float64}:  -0.16666666666666666  -0.16666666666666666   0.16666666666666666   0.16666666666666666

julia> grid_y[rows] 4-element Vector{Float64}:  -0.16666666666666666   0.16666666666666666  -0.16666666666666666   0.16666666666666666
```
