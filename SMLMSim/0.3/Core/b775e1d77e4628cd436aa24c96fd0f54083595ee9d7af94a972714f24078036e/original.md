```
uniform3D(ρ::Float64, p::Pattern3D, field_x::Float64, field_y::Float64; 
         zrange::Vector{Float64}=[-1.0, 1.0])
```

Create coordinate arrays for randomly placed and rotated 3D patterns.

# Arguments

  * `ρ::Float64`: Pattern density (patterns per square micron)
  * `p::Pattern3D`: Pattern to replicate
  * `field_x::Float64`: Field width in microns
  * `field_y::Float64`: Field height in microns
  * `zrange::Vector{Float64}=[-1.0, 1.0]`: [min*z, max*z] range in microns

# Returns

  * `Tuple{Vector{Float64}, Vector{Float64}, Vector{Float64}}`: (x, y, z) coordinates

# Example

```julia
# Generate coordinates for randomly placed Nmer3D patterns
nmer = Nmer3D(; n=6, d=0.2)
x, y, z = uniform3D(1.0, nmer, 10.0, 10.0; zrange=[-2.0, 2.0])
```
