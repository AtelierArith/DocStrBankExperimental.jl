```
mapc(f, rgb) -> rgbf
mapc(f, rgb1, rgb2) -> rgbf
```

`mapc` は入力色の各カラーチャンネルに関数 `f` を適用し、同じカラースペースで出力色を返します。

# 例:

```
julia> mapc(x->clamp(x,0,1), RGB(-0.2,0.3,1.2))
RGB{Float64}(0.0,0.3,1.0)

julia> mapc(max, RGB(0.1,0.8,0.3), RGB(0.5,0.5,0.5))
RGB{Float64}(0.5,0.8,0.5)

julia> mapc(+, RGB(0.1,0.8,0.3), RGB(0.5,0.5,0.5))
RGB{Float64}(0.6,1.3,0.8)
```
