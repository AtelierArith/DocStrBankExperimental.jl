```
move_i(shape, i)
```

`shape`をi軸（垂直軸）に沿ってiピクセル移動させた形状を返します。

関連項目としては [`move_j`](@ref)、[`move`](@ref) があります。

# 例

```julia-repl
julia> move_i(Line(Point(9, 5), Point(24, 28)), 2)
Line{Int64}(Point{Int64}(11, 5), Point{Int64}(26, 28))
```
