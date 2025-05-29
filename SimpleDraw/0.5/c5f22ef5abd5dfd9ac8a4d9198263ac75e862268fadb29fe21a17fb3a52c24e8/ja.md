```
get_i_max(image::AbstractMatrix)
```

`image`に沿ったi軸（縦軸、1軸）の最後のインデックスを返します。

# 例

```julia-repl
julia> get_i_max(falses(32, 64))
32
```
