```
uniform2D(ρ::Float64, p::Pattern2D, field_x::Float64, field_y::Float64)
```

Create coordinate arrays for randomly placed and rotated 2D patterns.

# Arguments

  * `ρ::Float64`: Pattern density (patterns per square micron)
  * `p::Pattern2D`: Pattern to replicate
  * `field_x::Float64`: Field width in microns
  * `field_y::Float64`: Field height in microns

# Returns

  * `Tuple{Vector{Float64}, Vector{Float64}}`: (x, y) coordinates in microns

# Example

```julia
# Generate coordinates for randomly placed Nmer2D patterns
nmer = Nmer2D(; n=6, d=0.2)
x, y = uniform2D(1.0, nmer, 10.0, 10.0)
```
