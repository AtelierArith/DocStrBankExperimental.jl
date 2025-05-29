```
draw!(img::AbstractArray{T,2}, verts::Vector{CartesianIndex{2}}, f::AbstractPolyFillAlgorithm; closed::Bool)
```

Draw on `img` using algorithm `f`.

# Output

When `img` is specified, changes are made on `img` and returned.

# Example

Just simply pass an algorithm with parameters, with image and vertices of polygon

```julia
using ImageDraw

img = zeros(RGB, 7, 7)
expected = copy(img)
expected[2:6, 2:6] .= RGB{N0f8}(1)

verts = [CartesianIndex(2, 2), CartesianIndex(2, 6), CartesianIndex(6, 6), CartesianIndex(6, 2), CartesianIndex(2,2)]

draw!(img, verts, BoundaryFill(4, 4; fill_value = RGB(1), boundary_value = RGB(1)); closed = true)
```
