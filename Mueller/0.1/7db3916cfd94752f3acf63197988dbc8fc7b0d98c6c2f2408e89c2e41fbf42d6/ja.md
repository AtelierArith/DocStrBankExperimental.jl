```
hwp([T=Float64], θ=0)
```

角度 `θ` で整列したファースト軸を持つ半波長板 (HWP)、単位はラジアンです。

# 例

```jldoctest
julia> M = hwp()
4×4 StaticArrays.SMatrix{4, 4, Float64, 16} with indices SOneTo(4)×SOneTo(4):
 1.0   0.0   0.0           0.0
 0.0   1.0   0.0           0.0
 0.0   0.0  -1.0          -1.22465e-16
 0.0  -0.0   1.22465e-16  -1.0

julia> S = [1, 1, 0, 0]; # I, Q, U, V

julia> M * S # +Qをそのまま通す
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
 1.0
 1.0
 0.0
 0.0

julia> rotate(M, π/8) * S # +Qを+Uに切り替える
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
  1.0
  1.9967346175427393e-16
  1.0
 -8.659560562354932e-17

```

# 参照

[`waveplate`](@ref), [`qwp`](@ref)
