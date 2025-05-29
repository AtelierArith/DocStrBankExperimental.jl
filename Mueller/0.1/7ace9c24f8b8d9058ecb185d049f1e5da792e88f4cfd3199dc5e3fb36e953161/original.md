```
qwp([T=Float64], θ=0)
```

A quarter-wave plate (QWP) with fast axis oriented at angle `θ`, in radians.

# Examples

```jldoctest
julia> M = qwp()
4×4 StaticArrays.SMatrix{4, 4, Float64, 16} with indices SOneTo(4)×SOneTo(4):
 1.0   0.0  0.0           0.0
 0.0   1.0  0.0           0.0
 0.0   0.0  6.12323e-17  -1.0
 0.0  -0.0  1.0           6.12323e-17

julia> S = [1, 1, 0, 0]; # I, Q, U, V

julia> M * S # allow +Q through unchanged
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
 1.0
 1.0
 0.0
 0.0

julia> qwp(-π/4) * S # switch +Q to +V
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
  1.0
  6.123233995736766e-17
 -6.123233995736765e-17
  1.0
```

# See also

[`waveplate`](@ref), [`hwp`](@ref)
