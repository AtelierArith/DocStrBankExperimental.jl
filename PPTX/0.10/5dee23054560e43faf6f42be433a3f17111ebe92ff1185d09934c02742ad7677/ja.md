```julia
Slide(
    shapes::Vector{AbstractShape}=AbstractShape[];
    title::String="",
    layout::Int=1,
)
```

  * `shapes::Vector{AbstractShape}` PowerPointに追加する形状で、後から追加することもできます
  * `title::String` スライドレイアウトにあるタイトルテキストボックス内に配置されるタイトルテキスト
  * `layout::Int` 使用するスライドレイアウト。通常、1はタイトルスライド、2はテキストスライドです。

PowerPointプレゼンテーションのためのスライドを作成します。

このスライドに`TextBox`や`Picture`などの任意の`AbstractShape`タイプを`push!`することができます。

# 例

```julia
julia> using PPTX

julia> slide = Slide(; title="Hello Title", layout=2)
Slide("Hello Title", PPTX.AbstractShape[], 0, 2)

julia> text = TextBox("Hello world!")
TextBox
 content is "Hello world!"
 offset_x is 1800000 EMUs
 offset_y is 1800000 EMUs
 size_x is 1440000 EMUs
 size_y is 1080000 EMUs

julia> push!(slide, text);

julia> slide
Slide("Hello Title", PPTX.AbstractShape[TextBox], 0, 2)

```
