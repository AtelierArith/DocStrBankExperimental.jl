```
se3ToVec(se3mat)
```

se3行列を空間速度ベクトルに変換します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> se3ToVec([0 -3 2 4; 3 0 -1 5; -2 1 0 6; 0 0 0 0])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
