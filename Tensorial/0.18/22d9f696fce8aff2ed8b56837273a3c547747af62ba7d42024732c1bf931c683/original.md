```
rotmat(a => b)
```

Construct rotation matrix rotating vector `a` to `b`. The norms of two vectors must be the same.

# Examples

```jldoctest
julia> a = normalize(rand(Vec{3}))
3-element Vec{3, Float64}:
 0.4829957515506539
 0.8135223859352438
 0.3238771859304809

julia> b = normalize(rand(Vec{3}))
3-element Vec{3, Float64}:
 0.8605677447967596
 0.3398133016944055
 0.3794075336718636

julia> R = rotmat(a => b)
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 -0.00540771   0.853773   0.520617
  0.853773    -0.267108   0.446905
  0.520617     0.446905  -0.727485

julia> R * a ≈ b
true
```
