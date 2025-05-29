```
cuboids(origin::Vector{<:Real}, dimension::Vector{<:Real}, color::String=""; opc::Real=1)

Creates a 3D box mesh centered at the given origin with specified dimensions and color.

# Arguments
- `origin::Vector{<:Real}`: A vector of three Reals specifying the center of the box.
- `dimension::Vector{<:Real}`: A vector of three Reals specifying the dimensions (width, height, depth) of the box.
- `color::String`: A string specifying the color of the box.

# Keywords
- `opc`: (optional) A Real specifying the opacity of the box. Default is 1.
```
