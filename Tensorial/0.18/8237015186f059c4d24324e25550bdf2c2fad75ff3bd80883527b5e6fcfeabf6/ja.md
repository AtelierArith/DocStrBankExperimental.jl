```
rotate(x::Vec, q::Quaternion)
```

クォータニオン `q` によって `x` を回転させます。

# 例

```jldoctest
julia> v = Vec(1.0, 0.0, 0.0)
3-element Vec{3, Float64}:
 1.0
 0.0
 0.0

julia> rotate(v, quaternion(π/4, Vec(0,0,1)))
3-element Vec{3, Float64}:
 0.7071067811865475
 0.7071067811865476
 0.0
```
