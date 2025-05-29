```
Rasterize(grid)
Rasterize(grid, var₁ => agg₁, ..., varₙ => aggₙ)
```

Rasterize geometries within specified `grid`.

```
Rasterize(nx, ny)
Rasterize(nx, ny, var₁ => agg₁, ..., varₙ => aggₙ)
```

Alternatively, use the grid with size `nx` by `ny` obtained with discretization of the bounding box.

Duplicates of a variable `varᵢ` are aggregated with aggregation function `aggᵢ`. If an aggregation function  is not defined for variable `varᵢ`, the default aggregation  function will be used. Default aggregation function is `mean` for continuous variables and `first` otherwise.

# Examples

```julia
grid = CartesianGrid(10, 10)
Rasterize(grid)
Rasterize(10, 10)
Rasterize(grid, 1 => last, 2 => maximum)
Rasterize(10, 10, 1 => last, 2 => maximum)
Rasterize(grid, :a => first, :b => minimum)
Rasterize(10, 10, :a => first, :b => minimum)
Rasterize(grid, "a" => last, "b" => maximum)
Rasterize(10, 10, "a" => last, "b" => maximum)
```
