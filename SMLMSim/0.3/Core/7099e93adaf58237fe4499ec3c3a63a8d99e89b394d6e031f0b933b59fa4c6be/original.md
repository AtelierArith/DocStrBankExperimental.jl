```
rotate!(p::Pattern2D, θ::Float64)
```

Rotate a 2D pattern by angle θ (in radians).

# Arguments

  * `p::Pattern2D`: Pattern to rotate
  * `θ::Float64`: Rotation angle in radians

# Example

```julia
nmer = Nmer2D()
rotate!(nmer, π/4)  # Rotate 45 degrees
```
