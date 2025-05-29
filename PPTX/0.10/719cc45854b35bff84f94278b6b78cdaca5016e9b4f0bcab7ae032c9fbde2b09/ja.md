```julia
function TextBox(;
    content::String = "",
    offset = (50,50), # ミリメートル
    offset_x = offset[1],
    offset_y = offset[2],
    size = (40,30), # ミリメートル
    size_x = size[1],
    size_y = size[2],
    hlink = nothing, # ハイパーリンク
    color = nothing, # 16進数文字列またはColorantを使用
    linecolor = nothing, # 16進数文字列またはColorantを使用
    linewidth = nothing, # ポイント単位の値を使用、例: 3
    rotation = nothing, # 度単位の値を使用、例: 90
    textstyle = (italic = false, bold = false, fontsize = nothing),
    margins = nothing, # 例: (left=0.1, right=0.1, bottom=0.1, top=0.1) ミリメートル単位
    wrap = false, # 形状内でテキストを折り返すかどうか
)
```

スライドで使用するためのTextBox。オフセットとサイズはミリメートル単位ですが、EMUに変換されます。

テキストスタイルのオプションについては、[`TextStyle`](@ref TextStyle)を参照してください。

# 例

```jldoctest
using PPTX

text = TextBox(
    content="Hello world!",
    offset=(100, 50),
    size=(30,50),
    textstyle=(color=:white, bold=true),
    color=:blue,
    linecolor=:black,
    linewidth=3
)

# 出力

TextBox
 content is "Hello world!"
 content.style has
  bold is true
  color is FFFFFF
 offset_x is 3600000 EMUs
 offset_y is 1800000 EMUs
 size_x is 1080000 EMUs
 size_y is 1800000 EMUs
 color is 0000FF
 linecolor is 000000
 linewidth is 38100 EMUs

```
