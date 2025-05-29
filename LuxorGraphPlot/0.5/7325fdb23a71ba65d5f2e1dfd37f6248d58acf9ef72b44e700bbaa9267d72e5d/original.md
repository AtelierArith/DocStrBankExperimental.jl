```
show_graph([f, ]graph::AbstractGraph;
    kwargs...
    )
```

Show a graph in VSCode, Pluto or Jupyter notebook, or save it to a file.

## Positional arguments

  * `f` is a function that returns extra `Luxor` plotting statements.
  * `graph` is a graph instance.
  * `locs` is a vector of tuples for specifying the vertex locations, or a [`AbstractLayout`](@ref) instance.

## Keyword arguments

  * `config` is a [`GraphDisplayConfig`](@ref) instance.
  * `vertex_colors` is a vector of color strings for specifying vertex fill colors.
  * `vertex_sizes` is a vector of real numbers for specifying vertex sizes.
  * `vertex_shapes` is a vector of strings for specifying vertex shapes, the string should be "circle" or "box".
  * `vertex_stroke_colors` is a vector of color strings for specifying vertex stroke colors.
  * `vertex_text_colors` is a vector of color strings for specifying vertex text colors.
  * `edge_colors` is a vector of color strings for specifying edge colors.
  * `texts` is a vector of strings for labeling vertices.

  * `padding_left::Int = 10`, the padding on the left side of the drawing
  * `padding_right::Int = 10`, the padding on the right side of the drawing
  * `padding_top::Int = 10`, the padding on the top side of the drawing
  * `padding_bottom::Int = 10`, the padding on the bottom side of the drawing
  * `format` is the output format, which can be `:svg`, `:png` or `:pdf`.
  * `filename` is a string as the output filename.

## Example

```jldoctest
julia> using Graphs, LuxorGraphPlot

julia> show_graph(smallgraph(:petersen); format=:png, vertex_colors=rand(["blue", "red"], 10));
```
