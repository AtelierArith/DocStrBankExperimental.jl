```
StructuredGrid(X, Y, Z, ...)
StructuredGrid{M,C}(X, Y, Z, ...)
```

A structured grid with vertices at sorted coordinates `X`, `Y`, `Z`, ..., manifold `M` (default to `𝔼`) and CRS type `C` (default to `Cartesian`).

## Examples

Create a 2D structured grid with regular spacing in `x` dimension and irregular spacing in `y` dimension:

```julia
julia> X = repeat(0.0:0.2:1.0, 1, 6)
julia> Y = repeat([0.0, 0.1, 0.3, 0.7, 0.9, 1.0]', 6, 1)
julia> StructuredGrid(X, Y)
```
