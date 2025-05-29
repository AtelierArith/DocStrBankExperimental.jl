```
slerp(qa::Quaternion, qb::Quaternion, t::Real)
```

入力 `qa` と `qb` の間の球面線形補間 (Slerp)。入力は関数内で正規化されるため、戻り値の絶対値は 1 になります。

# 例

```jldoctest
julia> using Quaternions

julia> qa = Quaternion(1,0,0,0)
Quaternion{Int64}(1, 0, 0, 0)

julia> qb = Quaternion(0,1,0,0)
Quaternion{Int64}(0, 1, 0, 0)

julia> slerp(qa, qb, 0.6)
QuaternionF64(0.5877852522924731, 0.8090169943749475, 0.0, 0.0)

julia> ans ≈ Quaternion(cospi(0.3), sinpi(0.3), 0, 0)
true
```
