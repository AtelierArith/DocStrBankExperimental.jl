```
round_sphere(diameter, ΔX0; kwargs...)
```

Create a grid of points distributed in a smooth sphere without edges on the surface with a specific `diameter` and the point spacing `ΔX0`. Internally, some parts of `TrixiParticles.jl` were copied and adapted for this function.

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
julia> position, volume = round_sphere(10, 2);

julia> position
3×63 Matrix{Float64}:
 0.0  1.74586  0.539501  -1.41243  -1.41243  …  -1.95518   -0.48289   1.35303   0.0
 0.0  0.0      1.66041    1.02619  -1.02619     -0.941566  -2.11568  -1.69664   0.0
 2.0  0.97569  0.97569    0.97569   0.97569     -3.36017   -3.36017  -3.36017  -4.0

julia> volume
63-element Vector{Float64}:
 8.311091676163475
 8.311091676163475
 8.311091676163475
 8.311091676163475
 8.311091676163475
 ⋮
 8.311091676163475
 8.311091676163475
 8.311091676163475
 8.311091676163475
```
