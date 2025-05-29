```julia
TextStyle(
    bold = false,
    italic = false,
    underscore = false,
    strike = false,
    fontsize = nothing,
    typeface = nothing, # or a string, like "Courier New"
    color = nothing, # anything compliant with Colors.jl
    align = nothing, # "left", "right" or "center"
)
```

Style of the text inside a `TextBox`. You can use Colors.jl colorants for the text color, or directly provide a HEX string, or a symbol like :white.

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
