```
create_cube(origin::Vector{<:Real}, dim::Real, ind::Int=1, mode::String="corner", fac::Real=2; render=false)

Creates a cube with the specified parameters.

# Arguments
- `origin::Vector{<:Real}`: The origin point of the cube.
- `dim::Real`: The side length of the cube.
- `ind::Int=1`: The color index of the cube.
- `mode::String="corner"`: The mode specifying the cube's origin ("corner" or "center").
- `fac::Real=2`: The interior densified factor according to the grid spacing.

# Keywords
- `render=false`: real-time rendering for creation/operation.
```
