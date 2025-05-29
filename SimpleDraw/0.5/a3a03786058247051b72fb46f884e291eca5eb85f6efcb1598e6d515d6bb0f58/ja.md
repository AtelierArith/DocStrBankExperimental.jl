```
move(shape, i, j)
```

`shape`をi軸（垂直軸）にiピクセル、j軸（水平軸）にjピクセル移動させた形状を返します。

[`move_i`](@ref)や[`move_j`](@ref)も参照してください。

# 例

```julia-repl
julia> move(Line(Point(9, 5), Point(24, 28)), 2, 3)
Line{Int64}(Point{Int64}(11, 8), Point{Int64}(26, 31))
```
