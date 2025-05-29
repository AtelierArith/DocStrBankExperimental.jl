Structure to represent piecewise linear data as a series of points: two points define one segment, three points define two segments, etc. The curve starts at the first point given, not the origin. Principally used for the representation of cost functions where the points store quantities (x, y), such as (MW, :/h).

# Arguments

  * `points::Vector{@NamedTuple{x::Float64, y::Float64}}`: the points that define the function
