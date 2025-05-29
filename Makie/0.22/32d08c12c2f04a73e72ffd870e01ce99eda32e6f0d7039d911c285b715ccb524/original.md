```
triplot(x, y; kwargs...)
triplot(positions; kwargs...)
triplot(triangles::Triangulation; kwargs...)
```

Plots a triangulation based on the provided position or `Triangulation` from DelaunayTriangulation.jl.

## Plot type

The plot type alias for the `triplot` function is `Triplot`.

## Attributes

**`bounding_box`** =  `automatic`  — Sets the bounding box for truncating ghost edges which can be a `Rect2` (or `BBox`) or a tuple of the form `(xmin, xmax, ymin, ymax)`. By default, the rectangle will be given by `[a - eΔx, b + eΔx] × [c - eΔy, d + eΔy]` where `e` is the `ghost_edge_extension_factor`, `Δx = b - a` and `Δy = d - c` are the lengths of the sides of the rectangle, and `[a, b] × [c, d]` is the bounding box of the points in the triangulation.

**`constrained_edge_color`** =  `:magenta`  — Sets the color of the constrained edges.

**`constrained_edge_linestyle`** =  `@inherit linestyle`  — Sets the linestyle of the constrained edges.

**`constrained_edge_linewidth`** =  `@inherit linewidth`  — Sets the width of the constrained edges.

**`convex_hull_color`** =  `:red`  — Sets the color of the convex hull.

**`convex_hull_linestyle`** =  `:dash`  — Sets the linestyle of the convex hull.

**`convex_hull_linewidth`** =  `@inherit linewidth`  — Sets the width of the convex hull.

**`ghost_edge_color`** =  `:blue`  — Sets the color of the ghost edges.

**`ghost_edge_extension_factor`** =  `0.1`  — Sets the extension factor for the rectangle that the exterior ghost edges are extended onto.

**`ghost_edge_linestyle`** =  `@inherit linestyle`  — Sets the linestyle of the ghost edges.

**`ghost_edge_linewidth`** =  `@inherit linewidth`  — Sets the width of the ghost edges.

**`joinstyle`** =  `@inherit joinstyle`  — *No docs available.*

**`linecap`** =  `@inherit linecap`  — *No docs available.*

**`linestyle`** =  `:solid`  — Sets the linestyle of triangle edges.

**`marker`** =  `@inherit marker`  — Sets the shape of the points.

**`markercolor`** =  `@inherit markercolor`  — Sets the color of the points.

**`markersize`** =  `@inherit markersize`  — Sets the size of the points.

**`miter_limit`** =  `@inherit miter_limit`  — *No docs available.*

**`recompute_centers`** =  `false`  — Determines whether to recompute the representative points for the ghost edge orientation. Note that this will mutate `tri.representative_point_list` directly.

**`show_constrained_edges`** =  `false`  — Determines whether to plot the constrained edges.

**`show_convex_hull`** =  `false`  — Determines whether to plot the convex hull.

**`show_ghost_edges`** =  `false`  — Determines whether to plot the ghost edges.

**`show_points`** =  `false`  — Determines whether to plot the individual points. Note that this will only plot points included in the triangulation.

**`strokecolor`** =  `@inherit patchstrokecolor`  — Sets the color of triangle edges.

**`strokewidth`** =  `1`  — Sets the linewidth of triangle edges.

**`triangle_color`** =  `:transparent`  — Sets the color of the triangles.
