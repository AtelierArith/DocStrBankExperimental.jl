```
get_i_min(shape)
```

`shape`のバウンディングボックスのi軸（垂直軸、1軸目）に沿った最小インデックスを返します。

関連情報として[`get_i_max`](@ref)、[`get_j_min`](@ref)、[`get_j_max`](@ref)を参照してください。

# 例

```julia-repl
julia> get_i_min(Line(Point(9, 5), Point(24, 28)))
9
```
