```
get_width(x)
```

`x`（形状または画像）の j 軸（水平軸、2 番目の軸）に沿った幅を返します。

関連情報として [`get_height`](@ref) も参照してください。

# 例

```julia-repl
julia> get_width(Line(Point(9, 5), Point(24, 28)))
24

julia> get_width(falses(32, 64))
64
```
