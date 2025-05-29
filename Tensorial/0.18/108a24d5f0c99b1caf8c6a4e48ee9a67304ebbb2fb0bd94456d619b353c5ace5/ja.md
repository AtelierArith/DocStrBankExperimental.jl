```
rotmat(θ, n::Vec)
```

角度 `θ` と軸 `n` から回転行列を構築します。

# 例

```jldoctest
julia> x = Vec(1.0, 0.0, 0.0)
3-element Vec{3, Float64}:
 1.0
 0.0
 0.0

julia> n = Vec(0.0, 0.0, 1.0)
3-element Vec{3, Float64}:
 0.0
 0.0
 1.0

julia> rotmat(π/2, n) * x
3-element Vec{3, Float64}:
 6.123233995736766e-17
 1.0
 0.0
```
