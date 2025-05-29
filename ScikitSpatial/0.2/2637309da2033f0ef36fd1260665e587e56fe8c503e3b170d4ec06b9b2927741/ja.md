```
distance(point_a::AbstractVector, point_b::AbstractVector) -> Float
```

点から直線までの距離を計算します。

これは、点から直線上のその投影までの距離です。

# 例

```jldoctest
julia> distance([0, 0], Line([0, 0], [1, 0]))
0.0

julia> round(distance([1, 0], Line([0, 0], [1, 1])), digits=3)
0.707

julia> round(distance([1, 2, 3], Line([-1, 3, 2], [7, 4, 2])), digits=3)
1.978
```
