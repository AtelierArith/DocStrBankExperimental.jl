```
square_image([T=Float32] r, c; l=nothing) where {T}

`r×c` 画像の中に `l×l` の正方形を作成します。

# 例

```

julia-repl julia> square_image(30, 30; l=10) 30×30 Array{Float32,2}: [...] ```
