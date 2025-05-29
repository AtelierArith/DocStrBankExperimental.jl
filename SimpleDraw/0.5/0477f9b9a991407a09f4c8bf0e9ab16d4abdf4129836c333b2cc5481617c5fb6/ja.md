```
get_height(x)
```

`x`（形状または画像）のi軸（垂直軸、1軸）に沿った高さを返します。

[`get_width`](@ref)も参照してください。

# 例

```julia-repl
julia> get_height(Line(Point(9, 5), Point(24, 28)))
16

julia> get_height(falses(32, 64))
32
```
