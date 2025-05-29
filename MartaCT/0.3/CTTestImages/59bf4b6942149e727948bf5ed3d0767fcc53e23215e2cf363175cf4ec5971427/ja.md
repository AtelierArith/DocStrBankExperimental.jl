```
circle_polar_image([T=Float32] nr, nϕ, radius; value=1) where {T}

半径 `radius` の円を極座標の `nr×nϕ` 画像内に作成します。

# 例

```

julia-repl julia> circle*polar*image(30, 30, 10) 30×30 Array{Float32,2}: [...] ```
