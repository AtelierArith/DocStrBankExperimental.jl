```
get_j_max(image::AbstractMatrix)
```

`image`に沿ったj軸（水平軸、2番目の軸）の最後のインデックスを返します。

# 例

```julia-repl
julia> get_j_max(falses(32, 64))
64
```
