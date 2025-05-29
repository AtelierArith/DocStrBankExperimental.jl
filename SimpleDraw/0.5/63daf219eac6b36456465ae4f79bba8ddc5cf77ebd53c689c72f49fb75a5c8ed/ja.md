```
get_j_min(shape)
```

`shape`の境界ボックスのj軸（水平軸、2番目の軸）に沿った最小インデックスを返します。

関連情報としては、[`get_j_max`](@ref)、[`get_i_min`](@ref)、[`get_i_max`](@ref)があります。

# 例

```julia-repl
julia> get_j_min(Line(Point(9, 5), Point(24, 28)))
5
```
