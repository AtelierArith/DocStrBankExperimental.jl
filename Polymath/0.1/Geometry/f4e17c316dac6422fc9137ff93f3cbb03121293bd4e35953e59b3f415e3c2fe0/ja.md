```
distance_2d(x1, y1, x2, y2)
distance_2d(p1, p2)
```

座標が与えられた2Dポイントのペア間の距離を計算します。

# 例

```julia-repl
julia> distance_2d(25, 42, 35, 80)
39.293765408777

julia> p1 = Point(25, 42)
Point(25, 42, nothing)

julia> p2 = Point(35, 80)
Point(35, 80, nothing)

julia> distance_2d(p1, p2)
39.293765408777
```
