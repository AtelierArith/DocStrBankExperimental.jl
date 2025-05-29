create_cylinder(origin::Vector{<:Real}, radius::Real, height::Real, ind::Int=1, fac::Real=2; render=false)

Creates a cylinder with the specified parameters.

# Arguments

  * `origin::Vector{<:Real}`: The base origin point of the cylinder.
  * `radius::Real`: The radius of the cylinder.
  * `height::Real`: The height of the cylinder.
  * `ind::Int=1`: The color index of the cylinder.
  * `fac::Real=2`: The interior densified factor according to the grid spacing.

# Keywords

  * `render=false`: real-time rendering for creation/operation.
