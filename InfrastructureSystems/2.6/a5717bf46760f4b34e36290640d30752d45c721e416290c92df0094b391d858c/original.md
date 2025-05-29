Structure to represent a step function as a series of endpoint x-coordinates and segment y-coordinates: two x-coordinates and one y-coordinate defines a single segment, three x-coordinates and two y-coordinates define two segments, etc. This can be useful to represent the derivative of a [PiecewiseLinearData](@ref), where the y-coordinates of this step function represent the slopes of that piecewise linear function, so there is also an optional field `c` that can be used to store the initial y-value of that piecewise linear function. Principally used for the representation of cost functions where the points store quantities (x, dy/dx), such as (MW, :/MWh).

# Arguments

  * `x_coords::Vector{Float64}`: the x-coordinates of the endpoints of the segments
  * `y_coords::Vector{Float64}`: the y-coordinates of the segments: `y_coords[1]` is the y-value between

`x_coords[1]` and `x_coords[2]`, etc. Must have one fewer elements than `x_coords`.

  * `c::Union{Nothing, Float64}`: optional, the value to use for the integral from 0 to `x_coords[1]` of this function
