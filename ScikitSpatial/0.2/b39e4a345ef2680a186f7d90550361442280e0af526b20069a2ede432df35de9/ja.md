```
distance(point_a::AbstractVector, point_b::AbstractVector) -> Float
```

2つの点の間の距離を計算します。

# 例

```jldoctest
julia> distance([0, 0], [0, 0])
0.0

julia> distance([1, 0], [0, 0])
1.0

julia> round(distance([1, 1], [2, 2]), digits=3)
1.414

julia> round(distance([0, 0, 0], [-1, -1, -1]), digits=3)
1.732
```
