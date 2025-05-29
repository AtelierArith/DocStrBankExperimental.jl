```
round_cylinder(diameter::Real, height::Real, ΔX0::Real; kwargs...)
```

Create a grid of  points distributed in a cylindrical shape with a specific `height` in z-dimension, a `diameter` and the point spacing `ΔX0`. Due to a concentric point distribution in the x-y-plane, there are no sharp edges that appear on the surface of the cylinder.

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
julia> position, volume = round_cylinder(5, 10, 2);

julia> position
3×30 Matrix{Float64}:
  1.5   0.463525  -1.21353   -1.21353   …  -1.21353   -1.21353    0.463525
  0.0   1.42658    0.881678  -0.881678      0.881678  -0.881678  -1.42658
 -5.0  -5.0       -5.0       -5.0           5.0        5.0        5.0

julia> volume
30-element Vector{Int64}:
 13.089969389957473
 13.089969389957473
 13.089969389957473
 13.089969389957473
 13.089969389957473
  ⋮
 13.089969389957473
 13.089969389957473
 13.089969389957473
 13.089969389957473
```
