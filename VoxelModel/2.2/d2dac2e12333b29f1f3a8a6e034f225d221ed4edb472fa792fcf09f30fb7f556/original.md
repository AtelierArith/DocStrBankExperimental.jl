create_sphere(origin::Vector{<:Real}, radius::Real, ind::Int=1, fac::Real=2; render=false)

Creates a sphere with the specified parameters.

# Arguments

  * `origin::Vector{<:Real}`: The origin point of the sphere.
  * `radius::Real`: The radius of the sphere.
  * `ind::Int=1`: The color index of the sphere.
  * `fac::Real=2`: The interior densified factor according to the grid spacing.

# Keywords

  * `render=false`: real-time rendering for creation/operation.
