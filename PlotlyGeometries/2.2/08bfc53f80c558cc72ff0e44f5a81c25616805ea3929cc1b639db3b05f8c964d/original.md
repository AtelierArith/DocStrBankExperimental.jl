```
squares(origin::Vector{<:Real}, side::Real, color::String="", mode::String="z"; opc::Real=1)

Creates a 2D square mesh centered at the given origin with the specified side length and color.

# Arguments
- `origin::Vector{<:Real}`: A vector of three Reals specifying the center of the square.
- `side::Real`: A Real specifying the side length of the square.
- `color::String`: A string specifying the color of the square.
- `mode`::String: (optional) A string specifying the orientation of the square ("x", "y", or "z"). Default is "z".

# Keywords
- `opc`: (optional) A Real specifying the opacity of the square. Default is 1.
```
