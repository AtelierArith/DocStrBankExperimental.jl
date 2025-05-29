```
get_j_min(image::AbstractMatrix)
```

`image`のj軸（水平軸、2番目の軸）に沿った最初のインデックスを返します。

# 例

```julia-repl
julia> get_j_min(falses(32, 64))
1
```
