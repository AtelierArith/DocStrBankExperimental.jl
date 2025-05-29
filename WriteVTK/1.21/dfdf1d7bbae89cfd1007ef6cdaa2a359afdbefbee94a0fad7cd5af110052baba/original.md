```
vtk_grid(filename, x::AbstractRange{T}, y::AbstractRange{T}, [z::AbstractRange{T}];
         kwargs...)
```

Create image data (`.vti`) file.

Along each direction, the grid is specified in terms of an AbstractRange object.

# Examples

```jldoctest
julia> vtk = vtk_grid("abc", 1:0.2:5, 2:1.:3, 4:1.:5)  # 3D dataset
VTK file 'abc.vti' (ImageData file, open)

julia> vtk = vtk_grid("abc", 1:5, 2:1.:3, range(4, 5; length = 3))  # different kinds of ranges
VTK file 'abc.vti' (ImageData file, open)

julia> vtk = vtk_grid("abc", 1:0.2:5, 2:1.:3)  # 2D dataset
VTK file 'abc.vti' (ImageData file, open)

julia> vtk = vtk_grid("def",
                      LinRange(0., 5., 10),
                      LinRange(0., 2π, 16),
                      LinRange(1., 10., 12))
VTK file 'def.vti' (ImageData file, open)

```
