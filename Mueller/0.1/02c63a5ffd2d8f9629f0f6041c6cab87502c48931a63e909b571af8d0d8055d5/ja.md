```
mirror([T=Float64], r=1, δ=π, θ=0)
```

反射ミラーは、反射率 `r` を持ち、光の基準フレームに対して角度 `θ` で、ラジアン単位で向けられ、位相シフト `δ` を持ちます。理想的なミラーは完璧な反射率と180°の位相シフトを持ちます。

# 例

```jldoctest
julia> M = mirror()
4×4 StaticArrays.SMatrix{4, 4, Float64, 16} with indices SOneTo(4)×SOneTo(4):
 1.0  0.0   0.0           0.0
 0.0  1.0   0.0          -0.0
 0.0  0.0  -1.0           1.22465e-16
 0.0  0.0  -1.22465e-16  -1.0

julia> S = [1, 1, 0, 0]; # I, Q, U, V

julia> M * S # 変化なし
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
 1.0
 1.0
 0.0
 0.0

julia> mirror(1, π, π/4) * S # 偏光光を回転
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
  1.0
 -1.0
  1.2246467991473532e-16
  1.2246467991473532e-16
```
