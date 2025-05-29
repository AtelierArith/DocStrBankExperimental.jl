```julia
TextStyle(
    bold = false,
    italic = false,
    underscore = false,
    strike = false,
    fontsize = nothing,
    typeface = nothing, # または "Courier New" のような文字列
    color = nothing, # Colors.jl に準拠した任意のもの
    align = nothing, # "left", "right" または "center"
)
```

`TextBox` 内のテキストのスタイル。テキストの色には Colors.jl のカラントを使用するか、直接 HEX 文字列を提供するか、:white のようなシンボルを使用できます。

```jldoctest
julia> using PPTX

julia> style = TextStyle(bold=true, color=:red)
TextStyle
 bold is true
 italic is false
 underscore is false
 strike is false
 fontsize is nothing
 typeface is nothing
 color is FF0000
 align is nothing

julia> text = TextBox(content = "hello"; style)
TextBox
 content is "hello"
 content.style has
  bold is true
  color is FF0000
 offset_x is 1800000 EMUs
 offset_y is 1800000 EMUs
 size_x is 1440000 EMUs
 size_y is 1080000 EMUs

```
