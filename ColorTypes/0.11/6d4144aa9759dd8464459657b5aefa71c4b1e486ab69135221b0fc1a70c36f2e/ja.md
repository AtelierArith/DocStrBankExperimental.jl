```
mapc(f, rgb) -> rgbf
mapc(f, rgb1, rgb2) -> rgbf
mapc(f, rgb1, rgb2, rgb3) -> rgbf
```

`mapc` は入力カラーの各色チャネルに関数 `f` を適用し、同じ色空間で出力カラーを返します。

# 例:

```
julia> mapc(x->clamp(x,0,1), RGB(-0.2,0.3,1.2))
RGB{Float64}(0.0,0.3,1.0)

julia> mapc(clamp, RGB(-0.2,0.3,1.2), RGB(0, 0.4, 0.5), RGB(1, 0.8, 0.7))
RGB{Float64}(0.0,0.4,0.7)

julia> mapc(max, RGB(0.1,0.8,0.3), RGB(0.5,0.5,0.5))
RGB{Float64}(0.5,0.8,0.5)

julia> mapc(+, RGB(0.1,0.8,0.3), RGB(0.5,0.5,0.5))
RGB{Float64}(0.6,1.3,0.8)
```
