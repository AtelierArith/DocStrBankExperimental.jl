```
rotmat(::Quaternion)
```

Construct rotation matrix from quaternion.

# Examples

```jldoctest
julia> q = quaternion(π/4, Vec(0,0,1))
0.9238795325112867 + 0.0𝙞 + 0.0𝙟 + 0.3826834323650898𝙠

julia> rotmat(q)
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.707107  -0.707107  0.0
 0.707107   0.707107  0.0
 0.0        0.0       1.0
```
