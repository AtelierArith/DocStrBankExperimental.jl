```
uniform_sphere(diameter, ΔX0; kwargs...)
```

Create a grid of uniformly distributed points in a sphere with a specific `diameter` and the point spacing `ΔX0`. Due to the uniform point spacings, edges on the surface of the sphere can occur.

# Arguments

  * `diameter::Real`: Diameter of the sphere.
  * `ΔX0::Real`: Spacing of the points.

# Keywords

  * `center`: The coordinates of the center of the sphere. Default: `(0, 0, 0)`

# Returns

  * `position::Matrix{Float64}`: A `3×n_points` matrix with the position of the points.
  * `volume::Vector{Float64}`: A vector with the volume of each point.

# Examples

```julia-repl
julia> position, volume = uniform_sphere(10, 2);

julia> position
3×81 Matrix{Float64}:
 -2.0   0.0   2.0  -2.0   0.0   2.0  -2.0  …   0.0   2.0  -2.0  0.0  2.0  -2.0  0.0  2.0
 -2.0  -2.0  -2.0   0.0   0.0   0.0   2.0     -2.0  -2.0   0.0  0.0  0.0   2.0  2.0  2.0
 -4.0  -4.0  -4.0  -4.0  -4.0  -4.0  -4.0      4.0   4.0   4.0  4.0  4.0   4.0  4.0  4.0

julia> volume
81-element Vector{Int64}:
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
