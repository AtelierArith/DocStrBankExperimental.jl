```
move_j(shape, j)
```

`shape`をjピクセルだけj軸（水平軸）に沿って移動させた形状を返します。

関連項目としては、[`move_i`](@ref)、[`move`](@ref)があります。

# 例

```julia-repl
julia> move_j(Line(Point(9, 5), Point(24, 28)), 3)
Line{Int64}(Point{Int64}(9, 8), Point{Int64}(24, 31))
```
