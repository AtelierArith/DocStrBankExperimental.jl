Given a graph and two vectors of X and Y coordinates, returns a Compose tree of the graph layout

**Arguments**

`G` Graph to draw

`layout` Optional. Layout algorithm. Currently can be one of [`random_layout`, `circular_layout`, `spring_layout`, `shell_layout`, `stressmajorize_layout`, `spectral_layout`]. Default: `spring_layout`

`locs_x, locs_y` Locations of the nodes. Can be any units you want, but will be normalized and centered anyway

`NODESIZE` Optional. Max size for the nodes. Default: `3.0/sqrt(N)`

`nodesize` Optional. Relative size for the nodes, can be a Vector. Default: `1.0`

`nodelabel` Optional. Labels for the vertices, a Vector or nothing. Default: `nothing`

`nodelabelc` Optional. Color for the node labels, can be a Vector. Default: `colorant"black"`

`nodelabeldist` Optional. Distances for the node labels from center of nodes. Default: `0.0`

`nodelabelangleoffset` Optional. Angle offset for the node labels. Default: `π/4.0`

`NODELABELSIZE` Optional. Largest fontsize for the vertice labels. Default: `4.0`

`nodelabelsize` Optional. Relative fontsize for the vertice labels, can be a Vector. Default: `1.0`

`nodefillc` Optional. Color to fill the nodes with, can be a Vector. Default: `colorant"turquoise"`

`nodestrokec` Optional. Color for the nodes stroke, can be a Vector. Default: `nothing`

`nodestrokelw` Optional. Line width for the nodes stroke, can be a Vector. Default: `0.0`

`edgelabel` Optional. Labels for the edges, a Vector or nothing. Default: `[]`

`edgelabelc` Optional. Color for the edge labels, can be a Vector. Default: `colorant"black"`

`edgelabeldistx, edgelabeldisty` Optional. Distance for the edge label from center of edge. Default: `0.0`

`EDGELABELSIZE` Optional. Largest fontsize for the edge labels. Default: `4.0`

`edgelabelsize` Optional. Relative fontsize for the edge labels, can be a Vector. Default: `1.0`

`EDGELINEWIDTH` Optional. Max line width for the edges. Default: `0.25/sqrt(N)`

`edgelinewidth` Optional. Relative line width for the edges, can be a Vector. Default: `1.0`

`edgestrokec` Optional. Color for the edge strokes, can be a Vector. Default: `colorant"lightgray"`

`arrowlengthfrac` Optional. Fraction of line length to use for arrows. Equal to 0 for undirected graphs. Default: `0.1` for the directed graphs

`arrowangleoffset` Optional. Angular width in radians for the arrows. Default: `π/9 (20 degrees)`
