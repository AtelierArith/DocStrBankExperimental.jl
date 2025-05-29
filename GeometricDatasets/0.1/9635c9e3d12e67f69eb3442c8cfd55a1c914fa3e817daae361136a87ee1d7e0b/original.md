Create a cube in R^(`dim``) with`n`points and radius`radius`.

# Arguments

  * `n::Integer`: the number of points.
  * `dim::Integer`: the dimension of the cube (that is: in which R^dim it is).
  * `radius::Number`: the "radius" of the cube, that is, the distance from the center to one of its sides..
  * `noise::Function`: a function such that `y = noise(dim)` is a `Vector{<:Number}` with `size(y) = (dim;)`.
