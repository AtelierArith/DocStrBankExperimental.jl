```
arrows(points, directions; kwargs...)
arrows(x, y, u, v)
arrows(x::AbstractVector, y::AbstractVector, u::AbstractMatrix, v::AbstractMatrix)
arrows(x, y, z, u, v, w)
```

Plots arrows at the specified points with the specified components. `u` and `v` are interpreted as vector components (`u` being the x and `v` being the y), and the vectors are plotted with the tails at `x`, `y`.

If `x, y, u, v` are `<: AbstractVector`, then each 'row' is plotted as a single vector.

If `u, v` are `<: AbstractMatrix`, then `x` and `y` are interpreted as specifications for a grid, and `u, v` are plotted as arrows along the grid.

`arrows` can also work in three dimensions.

## Attributes

Available attributes and their defaults for `AbstractPlotting.Combined{AbstractPlotting.arrows!}` are: 

```

```
