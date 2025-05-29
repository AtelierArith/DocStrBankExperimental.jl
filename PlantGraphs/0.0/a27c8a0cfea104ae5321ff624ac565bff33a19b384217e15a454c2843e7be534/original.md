```
draw(g::Graph; resolution = (1920, 1080), nlabels_textsize = 15, arrow_size = 15,
     node_size = 5)
```

Visualize a graph as network diagram.

## Arguments

  * `g::Graph`: The graph to be visualized.

## Keywords

  * `resolution = (1920, 1080)`: The resolution of the image to be rendered, in pixels (online relevant for native and web backends). Default resolution is HD.
  * `nlabels_textsize = 15`: Customize the size of the labels in the diagram.
  * `arrow_size = 15`: Customize the size of the arrows representing edges in the diagram.
  * `node_size = 5`: Customize the size of the nodes in the diagram.

## Details

By default, nodes are labelled with the type of data stored and their unique ID. See function `node_label()` to customize the label for different types of data.

See `save` from FileIO to export the network diagram as a raster or vector image (depending on the backend). The function `calculate_resolution()` can be useful to ensure a particular dpi of the exported image (assuming some physical size).

The graphics backend will interact with the environment where the Julia code is being executed (i.e., terminal, IDE such as VS Code, interactive notebook such as Jupyter or Pluto). These interactions are all controlled by the graphics package Makie that VPL relies on. Some details on the expected behavior specific to `draw()` can be found in the general VPL documentation.

## Returns

This function returns a Makie `Figure` object, while producing the visualization as a side effect.

## Examples

```jldoctest
julia> struct A1 <: Node val::Int end;

julia> struct B1 <: Node val::Int end;

julia> axiom = A1(1) + (B1(1) + A1(3), B1(4));

julia> g = Graph(axiom = axiom);

julia> import CairoMakie; # or GLMakie, WGLMakie, etc.

julia> draw(g);
```
