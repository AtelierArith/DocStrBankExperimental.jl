```
uniform_box(lx, ly, lz, ΔX0; kwargs...)
```

Create a grid of uniformly distributed points in a cuboid with lengths `lx`, `ly` and `lz` and point spacing `ΔX0`.

# Arguments

  * `lx::Real`: Length in x-dimension.
  * `ly::Real`: Length in y-dimension.
  * `lz::Real`: Length in z-dimension.
  * `ΔX0::Real`: Spacing of the points.

# Keywords

  * `center`: The coordinates of the center of the cuboid. Default: `(0, 0, 0)`

# Returns

  * `position::Matrix{Float64}`: A `3×n_points` matrix with the position of the points.
  * `volume::Vector{Float64}`: A vector with the volume of each point.

# Examples

```julia-repl
julia> position, volume = uniform_box(10, 10, 10, 2);

julia> position
3×125 Matrix{Float64}:
 -4.0  -2.0   0.0   2.0   4.0  -4.0  -2.0  …  0.0  2.0  4.0  -4.0  -2.0  0.0  2.0  4.0
 -4.0  -4.0  -4.0  -4.0  -4.0  -2.0  -2.0     2.0  2.0  2.0   4.0   4.0  4.0  4.0  4.0
 -4.0  -4.0  -4.0  -4.0  -4.0  -4.0  -4.0     4.0  4.0  4.0   4.0   4.0  4.0  4.0  4.0

julia> volume
125-element Vector{Int64}:
 8
 8
 8
 8
 ⋮
 8
 8
 8
 8
```
