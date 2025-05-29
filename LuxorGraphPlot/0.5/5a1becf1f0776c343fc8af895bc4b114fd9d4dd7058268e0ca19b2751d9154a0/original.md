```
GraphDisplayConfig
```

The configuration for graph display.

## Keyword arguments

  * `locs` is a vector of tuples for specifying the vertex locations.
  * `edges` is a vector of tuples for specifying the edges.
  * `fontsize::Float64 = 12.0`, the font size
  * `fontface::String = ""`, the font face, leave empty to follow system
  * `vertex_text_color = "black"`, the default text color
  * `vertex_stroke_color = "black"`, the default stroke color for vertices
  * `vertex_color = "transparent"`, the default default fill color for vertices
  * `vertex_size::Float64 = 10.0`, the default vertex size
  * `vertex_shape::Symbol = :circle`, the default vertex shape, which can be :circle, :box or :dot
  * `vertex_line_width::Float64 = 1`, the default vertex stroke line width
  * `vertex_line_style::String = "solid"`, the line style of vertex stroke, which can be one of ["solid", "dotted", "dot", "dotdashed", "longdashed", "shortdashed", "dash", "dashed", "dotdotdashed", "dotdotdotdashed"]
  * `edge_color = "black"`, the default edge color
  * `edge_line_width::Float64 = 1`, the default line width
  * `edge_style::String = "solid"`, the line style of edges, which can be one of ["solid", "dotted", "dot", "dotdashed", "longdashed", "shortdashed", "dash", "dashed", "dotdotdashed", "dotdotdotdashed"]
