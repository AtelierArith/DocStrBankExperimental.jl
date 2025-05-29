create_ellipsoid(origin::Vector{<:Real}, par::Vector{<:Real}, ind::Int=1, fac::Real=2; render=false)

Creates an ellipsoid with the specified parameters.

# Arguments

  * `origin::Vector{<:Real}`: The origin point of the ellipsoid.
  * `par::Vector{<:Real}`: The lengths of the semi-axes.
  * `ind::Int=1`: The color index of the ellipsoid.
  * `fac::Real=2`: The interior densified factor according to the grid spacing.

# Keywords

  * `render=false`: real-time rendering for creation/operation.
