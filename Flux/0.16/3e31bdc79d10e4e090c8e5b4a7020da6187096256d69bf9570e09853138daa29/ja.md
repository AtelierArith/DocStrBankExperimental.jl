```
DepthwiseConv(filter, in => out, σ=identity; stride=1, pad=0, dilation=1, [bias, init])
DepthwiseConv(weight::AbstractArray, [bias, activation; stride, pad, dilation])

入力チャネルの数と等しいグループ数を持つ[`Conv`](@ref)レイヤーである深さ方向畳み込み層を返します。

引数の説明については[`Conv`](@ref)を参照してください。

# 例

```

jldoctest julia> xs = rand(Float32, 100, 100, 3, 50);  # 50枚のRGB画像のバッチ

julia> layer = DepthwiseConv((5,5), 3 => 6, relu; bias=false) Conv((5, 5), 3 => 6, relu, groups=3, bias=false)  # 150パラメータ 

julia> layer(xs) |> size (96, 96, 6, 50)

julia> DepthwiseConv((5, 5), 3 => 9, stride=2, pad=2)(xs) |> size (50, 50, 9, 50) ```
