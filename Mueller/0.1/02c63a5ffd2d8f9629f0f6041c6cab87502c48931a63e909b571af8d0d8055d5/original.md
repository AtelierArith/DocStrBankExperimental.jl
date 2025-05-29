```
mirror([T=Float64], r=1, δ=π, θ=0)
```

A reflective mirror with reflectance `r`, oriented at angle `θ`, in radians, compared to the reference frame of the light, and with phase shift `δ`. An ideal mirror will have perfect reflectance and a 180° phase shift.

# Examples

```jldoctest
julia> M = mirror()
4×4 StaticArrays.SMatrix{4, 4, Float64, 16} with indices SOneTo(4)×SOneTo(4):
 1.0  0.0   0.0           0.0
 0.0  1.0   0.0          -0.0
 0.0  0.0  -1.0           1.22465e-16
 0.0  0.0  -1.22465e-16  -1.0

julia> S = [1, 1, 0, 0]; # I, Q, U, V

julia> M * S # no change
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
 1.0
 1.0
 0.0
 0.0

julia> mirror(1, π, π/4) * S # rotates polarized light
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
  1.0
 -1.0
  1.2246467991473532e-16
  1.2246467991473532e-16
```
