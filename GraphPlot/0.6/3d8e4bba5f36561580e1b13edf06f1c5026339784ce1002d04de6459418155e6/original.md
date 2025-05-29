Given a graph and two vectors of X and Y coordinates, returns a Compose tree of the graph layout

**Arguments**

`G` Graph to draw

`locs_x, locs_y` Locations of the nodes. Can be any units you want, but will be normalized and centered anyway. If not provided, will be obtained from `layout` kwarg.

**Keyword Arguments**

`layout` Layout algorithm. Currently can be one of [`random_layout`, `circular_layout`, `spring_layout`, `shell_layout`, `stressmajorize_layout`, `spectral_layout`]. Default: `spring_layout`

`title` Plot title. Default: `""`

`title_color` Plot title color. Default: `colorant"black"`

`title_size` Plot title size. Default: `4.0`

`font_family` Font family for all text. Default: `"Helvetica"`

`NODESIZE` Max size for the nodes. Default: `3.0/sqrt(N)`

`nodesize` Relative size for the nodes, can be a Vector. Default: `1.0`

`nodelabel` Labels for the vertices, a Vector or nothing. Default: `nothing`

`nodelabelc` Color for the node labels, can be a Vector. Default: `colorant"black"`

`nodelabeldist` Distances for the node labels from center of nodes. Default: `0.0`

`nodelabelangleoffset` Angle offset for the node labels. Default: `π/4.0`

`NODELABELSIZE` Largest fontsize for the vertex labels. Default: `4.0`

`nodelabelsize` Relative fontsize for the vertex labels, can be a Vector. Default: `1.0`

`nodefillc` Color to fill the nodes with, can be a Vector. Default: `colorant"turquoise"`

`nodestrokec` Color for the nodes stroke, can be a Vector. Default: `nothing`

`nodestrokelw` Line width for the nodes stroke, can be a Vector. Default: `0.0`

`edgelabel` Labels for the edges, a Vector or nothing. Default: `[]`

`edgelabelc` Color for the edge labels, can be a Vector. Default: `colorant"black"`

`edgelabeldistx, edgelabeldisty` Distance for the edge label from center of edge. Default: `0.0`

`EDGELABELSIZE` Largest fontsize for the edge labels. Default: `4.0`

`edgelabelsize` Relative fontsize for the edge labels, can be a Vector. Default: `1.0`

`EDGELINEWIDTH` Max line width for the edges. Default: `0.25/sqrt(N)`

`edgelinewidth` Relative line width for the edges, can be a Vector. Default: `1.0`

`edgestrokec` Color for the edge strokes, can be a Vector. Default: `colorant"lightgray"`

`arrowlengthfrac` Fraction of line length to use for arrows. Equal to 0 for undirected graphs. Default: `0.1` for the directed graphs

`arrowangleoffset` Angular width in radians for the arrows. Default: `π/9 (20 degrees)`

`linetype` Type of line used for edges ("straight", "curve"). Default: "straight"

`outangle` Angular width in radians for the edges (only used if `linetype = "curve`).  Default: `π/5 (36 degrees)`

`background_color` Color for the plot background. Default: `nothing`

`plot_size` Tuple of measures for width x height for plot area. Default: `(10cm, 10cm)`

`leftpad, rightpad, toppad, bottompad` Padding for the plot margins. Default: `0mm`

`pad` Padding for plot margins (overrides individual padding if given). Default: `nothing`
