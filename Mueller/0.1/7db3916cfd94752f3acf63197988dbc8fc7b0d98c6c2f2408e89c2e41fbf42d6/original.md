```
hwp([T=Float64], θ=0)
```

A half-wave plate (HWP) with fast axis oriented at angle `θ`, in radians.

# Examples

```jldoctest
julia> M = hwp()
4×4 StaticArrays.SMatrix{4, 4, Float64, 16} with indices SOneTo(4)×SOneTo(4):
 1.0   0.0   0.0           0.0
 0.0   1.0   0.0           0.0
 0.0   0.0  -1.0          -1.22465e-16
 0.0  -0.0   1.22465e-16  -1.0

julia> S = [1, 1, 0, 0]; # I, Q, U, V

julia> M * S # allow +Q through unchanged
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
 1.0
 1.0
 0.0
 0.0

julia> rotate(M, π/8) * S # switch +Q to +U
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
  1.0
  1.9967346175427393e-16
  1.0
 -8.659560562354932e-17

```

# See also

[`waveplate`](@ref), [`qwp`](@ref)
