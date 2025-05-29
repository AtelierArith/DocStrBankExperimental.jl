```
get_j_max(shape)
```

`shape`のj軸（水平軸、2番目の軸）に沿ったバウンディングボックスの最大インデックスを返します。

関連情報として[`get_j_min`](@ref)、[`get_i_min`](@ref)、[`get_i_max`](@ref)を参照してください。

# 例

```julia-repl
julia> get_j_max(Line(Point(9, 5), Point(24, 28)))
28
```
