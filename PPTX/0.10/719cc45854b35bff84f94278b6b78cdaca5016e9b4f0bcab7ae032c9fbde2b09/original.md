```julia
function TextBox(;
    content::String = "",
    offset = (50,50), # millimeters
    offset_x = offset[1],
    offset_y = offset[2],
    size = (40,30), # millimeters
    size_x = size[1],
    size_y = size[2],
    hlink = nothing, # hyperlink
    color = nothing, # use hex string, or Colorant
    linecolor = nothing, # use hex string, or Colorant
    linewidth = nothing, # use value in points, e.g. 3
    rotation = nothing, # use a value in degrees, e.g. 90
    textstyle = (italic = false, bold = false, fontsize = nothing),
    margins = nothing, # e.g. (left=0.1, right=0.1, bottom=0.1, top=0.1) in millimeters
    wrap = false, # wrap text in shape or not
)
```

A TextBox to be used on a Slide. Offsets and sizes are in millimeters, but will be converted to EMU.

See [`TextStyle`](@ref TextStyle) for more text style options.

# Examples

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

# output

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
