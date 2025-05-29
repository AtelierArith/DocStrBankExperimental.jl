```julia
(columns, rows) = find_grid_inpolygon(grid_x, grid_y, poly_x, poly_y)
```

Find the indexes of grid points that fall within a polygon for a grid with cell centers given by grid*x (j-columns of grid) and grid*y (i-rows of grid). Returns a list of rows and columns in the polygon

### Examples

```julia julia> grid_x = -1.5:1/3:1.5;

julia> grid_y = -1.5:1/3:1.5;

julia> cols,rows = find*grid*inpolygon(gridx, gridy, [-.4,.4,.4,-.4],[.4,.4,-.4,-.4]) ([5, 5, 6, 6], [5, 6, 5, 6])

julia> grid_x[cols] 4-element Vector{Float64}:  -0.16666666666666666  -0.16666666666666666   0.16666666666666666   0.16666666666666666

julia> grid_y[rows] 4-element Vector{Float64}:  -0.16666666666666666   0.16666666666666666  -0.16666666666666666   0.16666666666666666
