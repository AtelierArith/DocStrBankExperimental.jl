Create a sphere in R^(`dim`) with `n` points and radius `radius`.

# Arguments

  * `n::Integer`: the number of points.
  * `dim::Integer`: the dimension of the sphere (that is: in which R^dim it is).
  * `radius::Number`: the radius of the sphere.
  * `noise::Function`: a function such that `y = noise(dim)` is a `Vector{<:Number}` with `size(y) = (dim;)`.
