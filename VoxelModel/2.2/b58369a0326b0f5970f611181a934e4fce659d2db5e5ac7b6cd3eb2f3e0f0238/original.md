```
create_cuboid(origin::Vector{<:Real}, dim::Vector{<:Real}, ind::Int=1, mode::String="corner", fac::Real=2; render=false)

Creates a cuboid with the specified parameters.

# Arguments
- `origin::Vector{<:Real}`: The origin point of the cuboid.
- `dim::Vector{<:Real}`: The dimensions of the cuboid.
- `ind::Int=1`: The color index of the cuboid.
- `mode::String="corner"`: The mode specifying the cuboid's origin ("corner" or "center").
- `fac::Real=2`: The interior densified factor according to the grid spacing.

# Keywords
- `render=false`: real-time rendering for creation/operation.
```
