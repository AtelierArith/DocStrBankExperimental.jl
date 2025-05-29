```
vtk_grid(filename::AbstractString,
         x::AbstractVector{T}, y::AbstractVector{T}, [z::AbstractVector{T}];
         kwargs...)
```

Create 2D or 3D rectilinear grid (`.vtr`) file.

Coordinates are specified by separate vectors `x`, `y`, `z`.

# Examples

```jldoctest
julia> vtk = vtk_grid("abc", [0., 0.2, 0.5], collect(-2.:0.2:3), [1., 2.1, 2.3])
VTK file 'abc.vtr' (RectilinearGrid file, open)
```
