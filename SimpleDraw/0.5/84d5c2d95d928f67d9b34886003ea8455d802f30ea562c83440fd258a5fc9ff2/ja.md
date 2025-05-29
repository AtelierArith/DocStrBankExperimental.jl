```
get_position(x)
```

`x`（形状または画像）の左上隅の位置に対応する `Point` を返します。

# 例

```julia-repl
julia> get_position(Line(Point(9, 5), Point(24, 28)))
Point{Int64}(9, 5)

julia> get_position(falses(32, 64))
Point{Int64}(1, 1)
```
