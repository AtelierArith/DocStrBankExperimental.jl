```
uniform_cylinder(diameter::Real, height::Real, ΔX0::Real; kwargs...)
```

Create a grid of uniformly distributed points in a cylindrical shape with a specific `height` in z-dimension, a `diameter` and the point spacing `ΔX0`. Due to the uniform point spacings, edges on the surface of the cylinder can occur.

# Arguments

  * `diameter::Real`: Diameter of the cylinder.
  * `height::Real`: Height of the cylinder.
  * `ΔX0::Real`: Spacing of the points.

# Keywords

  * `center`: The coordinates of the center of the cylinder. Default: `(0, 0, 0)`

# Returns

  * `position::Matrix{Float64}`: A `3×n_points` matrix with the position of the points.
  * `volume::Vector{Float64}`: A vector with the volume of each point.

# Examples

```julia-repl
julia> position, volume = uniform_cylinder(5, 10, 2);

julia> position
3×20 Matrix{Float64}:
 -1.0   1.0  -1.0   1.0  -1.0   1.0  -1.0  …   1.0  -1.0  1.0  -1.0   1.0  -1.0  1.0
 -1.0  -1.0   1.0   1.0  -1.0  -1.0   1.0     -1.0   1.0  1.0  -1.0  -1.0   1.0  1.0
 -4.0  -4.0  -4.0  -4.0  -2.0  -2.0  -2.0      2.0   2.0  2.0   4.0   4.0   4.0  4.0

julia> volume
20-element Vector{Int64}:
 8
 8
 8
 8
 8
 ⋮
 8
 8
 8
 8
 8
```
