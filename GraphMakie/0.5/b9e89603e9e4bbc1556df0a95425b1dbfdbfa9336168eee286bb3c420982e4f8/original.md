```
graphplot(graph::AbstractGraph)
graphplot!(ax, graph::AbstractGraph)
```

Creates a plot of the network `graph`. Consists of multiple steps:

  * Layout the nodes: see `layout` attribute. The node position is accessible from outside the plot object `p` as an observable using `p[:node_pos]`.
  * plot edges as `edgeplot`-plot
  * if `arrow_show` plot arrowheads as `scatter`-plot
  * plot nodes as `scatter`-plot
  * if `nlabels!=nothing` plot node labels as `text`-plot
  * if `elabels!=nothing` plot edge labels as `text`-plot

The main attributes for the subplots are exposed as attributes for `graphplot`. Additional attributes for the `scatter`, `edgeplot` and `text` plots can be provided as a named tuples to `node_attr`, `edge_attr`, `nlabels_attr` and `elabels_attr`.

Most of the arguments can be either given as a vector of length of the edges/nodes or as a single value. One might run into errors when changing the underlying graph and therefore changing the number of Edges/Nodes.

## Attributes

### Main attributes

  * `layout=Spring()`: function `AbstractGraph->Vector{Point}` or `Vector{Point}` that determines the base layout.  Can also be any network layout from [NetworkLayout.jl](https://https://github.com/JuliaGraphs/NetworkLayout.jl), like `Spring`, `Stress`, `Spectral`, etc.
  * `node_color=automatic`: Defaults to `scatter_theme.color` in absence of `ilabels`.
  * `node_size=automatic`: Defaults to `scatter_theme.markersize` in absence of `ilabels`. Otherwise choses node size based on `ilabels` size.
  * `node_marker=automatic`: Defaults to `scatter_theme.marker` in absence of `ilabels`.
  * `node_strokewidth=automatic` Defaults to `scatter_theme.strokewidth` in absence of `ilabels`.
  * `node_attr=(;)`: List of kw arguments which gets passed to the `scatter` command
  * `edge_color=lineseg_theme.color`: Color for edges.
  * `edge_width=lineseg_theme.linewidth`: Pass a vector with 2 width per edge to get pointy edges.
  * `edge_attr=(;)`: List of kw arguments which gets passed to the `linesegments` command
  * `arrow_show=Makie.automatic`: `Bool`, indicate edge directions with arrowheads? Defaults to `Graphs.is_directed(graph)`.
  * `arrow_marker='➤'`
  * `arrow_size=scatter_theme.markersize`: Size of arrowheads.
  * `arrow_shift=0.5`: Shift arrow position from source (0) to dest (1) node.  If `arrow_shift=:end`, the arrowhead will be placed on the surface of the destination node  (assuming the destination node is circular).
  * `arrow_attr=(;)`: List of kw arguments which gets passed to the `scatter` command

### Node labels

The position of each label is determined by the node position plus an offset in data space.

  * `nlabels=nothing`: `Vector{String}` with label for each node
  * `nlabels_align=(:left, :bottom)`: Anchor of text field.
  * `nlabels_distance=0.0`: Pixel distance from node in direction of align.
  * `nlabels_color=labels_theme.color`
  * `nlabels_offset=nothing`: `Point` or `Vector{Point}` (in data space)
  * `nlabels_fontsize=labels_theme.fontsize`
  * `nlabels_attr=(;)`: List of kw arguments which gets passed to the `text` command

### Inner node labels

Put labels inside the marker. If labels are provided, change default attributes to `node_marker=Circle`, `node_strokewidth=1` and `node_color=:gray80`. The `node_size` will match size of the `ilabels`.

  * `ilabels=nothing`: `Vector` with label for each node
  * `ilabels_color=labels_theme.color`
  * `ilabels_fontsize=labels_theme.fontsize`
  * `ilabels_attr=(;)`: List of kw arguments which gets passed to the `text` command

### Edge labels

The base position of each label is determined by `src + shift*(dst-src)`. The additional `distance` parameter is given in pixels and shifts the text away from the edge.

  * `elabels=nothing`: `Vector{String}` with label for each edge
  * `elabels_align=(:center, :center)`: Anchor of text field.
  * `elabels_side = :left`: Side of the edge to put the edge label text
  * `elabels_distance=Makie.automatic`: Pixel distance of anchor to edge. The direction is decided based on `elabels_side`
  * `elabels_shift=0.5`: Position between src and dst of edge.
  * `elabels_rotation=Makie.automatic`: Angle of text per label. If `nothing` this will be determined by the edge angle. If `automatic` it will also point upwards making it easy to read.
  * `elabels_offset=nothing`: Additional offset in data space
  * `elabels_color=labels_theme.color`
  * `elabels_fontsize=labels_theme.fontsize`
  * `elabels_attr=(;)`: List of kw arguments which gets passed to the `text` command

### Curvy edges & self edges/loops

  * `edge_plottype=Makie.automatic()`: Either `automatic`, `:linesegments` or `:beziersegments`. `:beziersegments` are much slower for big graphs!

Self edges / loops: 

  * `selfedge_size=Makie.automatic()`: Size of selfloop (dict/vector possible).
  * `selfedge_direction=Makie.automatic()`: Direction of center of the selfloop as `Point2` (dict/vector possible).
  * `selfedge_width=Makie.automatic()`: Opening of selfloop in rad (dict/vector possible).
  * Note: If valid waypoints are provided for selfloops, the selfedge attributes above will be ignored.

High level interface for curvy edges:

  * `curve_distance=0.1`:

    Specify a distance of the (now curved) line to the straight line *in data   space*. Can be single value, array or dict. User provided `tangents` or   `waypoints` will overrule this property.
  * `curve_distance_usage=Makie.automatic()`:

    If `Makie.automatic()`, only plot double edges in a curvy way. Other options   are `true` and `false`.

Tangents interface for curvy edges:

  * `tangents=nothing`:

    Specify a pair of tangent vectors per edge (for src and dst). If `nothing`   (or edge idx not in dict) draw a straight line.
  * `tfactor=0.6`:

    Factor is used to calculate the bezier waypoints from the (normalized) tangents.   Higher factor means bigger radius. Can be tuple per edge to specify different   factor for src and dst.
  * Note: Tangents are ignored on selfloops if no waypoints are provided.

Waypoints along edges:

  * `waypoints=nothing`

    Specify waypoints for edges. This parameter should be given as a vector or   dict. Waypoints will be crossed using natural cubic splines. The waypoints may   or may not include the src/dst positions.
  * `waypoint_radius=nothing`

    If the attribute `waypoint_radius` is `nothing` or `:spline` the waypoints will    be crossed using natural cubic spline interpolation. If number (dict/vector    possible), the waypoints won't be reached, instead they will be connected with    straight lines which bend in the given radius around the waypoints.
