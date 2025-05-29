```
rotate!(p::Pattern3D, α::Float64, β::Float64, γ::Float64)
```

Rotate a 3D pattern by Euler angles α, β, γ (in radians). Uses ZYZ convention.

# Arguments

  * `p::Pattern3D`: Pattern to rotate
  * `α::Float64`: First rotation angle (around Z axis)
  * `β::Float64`: Second rotation angle (around Y' axis)
  * `γ::Float64`: Third rotation angle (around Z'' axis)

# Example

```julia
nmer = Nmer3D()
rotate!(nmer, π/4, π/6, π/3)
```
