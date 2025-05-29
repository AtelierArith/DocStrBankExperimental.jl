```
show_einsum(ein::AbstractEinsum;
    tensor_locs=nothing,
    label_locs=nothing,  # dict
    spring::Bool=true,
    optimal_distance=25.0,

    tensor_size=15,
    tensor_color="black",
    tensor_text_color="white",
    annotate_tensors=false,

    label_size=7,
    label_color="black",
    open_label_color="black",
    annotate_labels=true,
    kwargs...
    )
```

## Positional arguments

  * `ein` is an Einsum contraction code (provided by package `OMEinsum`).

## Keyword arguments

  * `locs` is a tuple of `tensor_locs` (vector) and `label_locs` (dict).
  * `spring` is switch to use spring method to optimize the location.
  * `optimal_distance` is a optimal distance parameter for `spring` optimizer.
  * `tensor_color` is a string to specify the color of tensor nodes.
  * `tensor_size` is a real number to specify the size of tensor nodes.
  * `tensor_text_color` is a color strings to specify tensor text color.
  * `annotate_tensors` is a boolean switch for annotate different tensors by integers.
  * `label_size` is a real number to specify label text node size.
  * `label_color` is a color strings to specify label text color.
  * `open_label_color` is a color strings to specify open label text color.
  * `annotate_labels` is a boolean switch for annotate different labels.
  * `format` is the output format, which can be `:svg`, `:png` or `:pdf`.
  * `filename` is a string as the output filename.

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
