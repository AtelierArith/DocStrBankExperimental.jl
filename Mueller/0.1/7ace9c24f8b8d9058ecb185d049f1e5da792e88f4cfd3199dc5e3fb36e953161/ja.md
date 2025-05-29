```
qwp([T=Float64], θ=0)
```

角度 `θ` で整列したファスト軸を持つ四分の一波長板 (QWP)、単位はラジアンです。

# 例

```jldoctest
julia> M = qwp()
4×4 StaticArrays.SMatrix{4, 4, Float64, 16} with indices SOneTo(4)×SOneTo(4):
 1.0   0.0  0.0           0.0
 0.0   1.0  0.0           0.0
 0.0   0.0  6.12323e-17  -1.0
 0.0  -0.0  1.0           6.12323e-17

julia> S = [1, 1, 0, 0]; # I, Q, U, V

julia> M * S # +Qをそのまま通す
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
 1.0
 1.0
 0.0
 0.0

julia> qwp(-π/4) * S # +Qを+Vに切り替える
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
  1.0
  6.123233995736766e-17
 -6.123233995736765e-17
  1.0
```

# 参照

[`waveplate`](@ref), [`hwp`](@ref)
