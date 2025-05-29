```
rotate!(p::Pattern3D, R::Matrix{Float64})
```

Rotate a 3D pattern by rotation matrix R.

# Arguments

  * `p::Pattern3D`: Pattern to rotate
  * `R::Matrix{Float64}`: 3x3 rotation matrix

# Example

```julia
nmer = Nmer3D()
# Create a rotation matrix for 90 degrees around z-axis
θ = π/2
R = [cos(θ) -sin(θ) 0; sin(θ) cos(θ) 0; 0 0 1]
rotate!(nmer, R)
```
