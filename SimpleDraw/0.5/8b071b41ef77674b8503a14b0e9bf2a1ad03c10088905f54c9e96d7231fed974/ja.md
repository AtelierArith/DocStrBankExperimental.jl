```
get_i_extrema(x)
```

`x`（形状または画像）の i 軸（縦軸、1 番目の軸）に沿った最小および最大インデックスを返します。

[`get_j_extrema`](@ref) も参照してください。

# 例

```julia-repl
julia> get_i_extrema(Line(Point(9, 5), Point(24, 28)))
(9, 24)

julia> get_i_extrema(falses(32, 64))
(1, 32)
```
