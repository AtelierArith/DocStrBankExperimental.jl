```julia
# Return SVector with the coordinates of the top right of a rectangle
using StaticArrays

function top_right(x::Float64, y::Float64, width::Float64, height::Float64)
    return SVector{x, y + height}
end
```
