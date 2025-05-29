```
get_i_min(image::AbstractMatrix)
```

`image`に沿ったi軸（垂直軸、1軸目）の最初のインデックスを返します。

# 例

```julia-repl
julia> get_i_min(falses(32, 64))
1
```
