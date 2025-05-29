```
get_j_extrema(x)
```

`x`（形状または画像）の j 軸（水平軸、2 番目の軸）に沿った最小および最大インデックスを返します。

関連情報は [`get_i_extrema`](@ref) を参照してください。

# 例

```julia-repl
julia> get_j_extrema(Line(Point(9, 5), Point(24, 28)))
(5, 28)

julia> get_j_extrema(falses(32, 64))
(1, 64)
```
