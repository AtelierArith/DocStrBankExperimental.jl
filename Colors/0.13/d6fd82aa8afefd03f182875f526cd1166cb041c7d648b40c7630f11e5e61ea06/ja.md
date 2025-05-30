```
weighted_color_mean(weights, colors)
```

与えられたコレクション `colors` の加重平均を `weights` で返します。これは `sum(weights .* colors)` の計算と意味的に同等です。

# 例

```jldoctest; setup = :(using Colors, FixedPointNumbers)
julia> rgbs = (RGB(1, 0, 0), RGB(0, 1, 0), RGB(0, 0, 1));

julia> weighted_color_mean([0.2, 0.2, 0.6], rgbs)
RGB{N0f8}(0.2, 0.2, 0.6)

julia> weighted_color_mean(0.5:-0.25:0.0, RGB{Float64}.(rgbs))
RGB{Float64}(0.5, 0.25, 0.0)
```

!!! compat "Colors v0.13"
    コレクションまたはイテレータ入力を持つ `weighted_color_mean` は、Colors v0.13 以降が必要です。


!!! note
    HSV のような円筒色空間では、三色以上の加重平均は一般的に意味がありません。

