```
RectilinearGrid(x, y, z, ...)
RectilinearGrid{M,C}(x, y, z, ...)
```

A rectilinear grid with vertices at sorted coordinates `x`, `y`, `z`, ..., manifold `M` (default to `𝔼`) and CRS type `C` (default to `Cartesian`).

## Examples

Create a 2D rectilinear grid with regular spacing in `x` dimension and irregular spacing in `y` dimension:

```julia
julia> x = 0.0:0.2:1.0
julia> y = [0.0, 0.1, 0.3, 0.7, 0.9, 1.0]
julia> RectilinearGrid(x, y)
```
