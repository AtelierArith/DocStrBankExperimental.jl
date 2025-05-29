```
so3ToVec(so3mat)
```

so(3) 表現を 3 ベクトルに変換します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> so3ToVec([0 -3 2; 3 0 -1; -2 1 0])
3-element Vector{Int64}:
 1
 2
 3
```
