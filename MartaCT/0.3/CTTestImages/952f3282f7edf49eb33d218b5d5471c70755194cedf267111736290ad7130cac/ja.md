```
circle_image([T=Float32]; radius=20, value=1) where {T}
```

与えられた値の円を持つ正方形の画像を作成します。

# 例

```julia-repl
julia> circle_image(30, 0.8)
30×30 Array{Float32,2}:
[...]
```

参照: [`gray_scale_image`](@ref), [`combine_images`](@ref)
