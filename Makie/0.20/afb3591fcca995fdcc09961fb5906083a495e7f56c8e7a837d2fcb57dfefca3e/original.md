```
triplot(x, y; kwargs...)
triplot(positions; kwargs...)
triplot(triangles::Triangulation; kwargs...)
```

Plots a triangulation based on the provided position or `Triangulation` from DelaunayTriangulation.jl.

## Attributes

  * `show_points = false` determines whether to plot the individual points. Note that this will only plot points included in the triangulation.
  * `show_convex_hull = false` determines whether to plot the convex hull.
  * `show_ghost_edges = false` determines whether to plot the ghost edges.
  * `show_constrained_edges = false` determines whether to plot the constrained edges.
  * `recompute_centers = false` determines whether to recompute the representative points for the ghost edge orientation. Note that this will mutate `tri.representative_point_list` directly.
  * `markersize = 12` sets the size of the points.
  * `marker = :circle` sets the shape of the points.
  * `markercolor = :black` sets the color of the points.
  * `strokecolor = :black` sets the color of triangle edges.
  * `strokewidth = 1` sets the linewidth of triangle edges.
  * `linestyle = :solid` sets the linestyle of triangle edges.
  * `triangle_color = (:white, 0.0)` sets the color of the triangles.
  * `convex_hull_color = :red` sets the color of the convex hull.
  * `convex_hull_linestyle = :dash` sets the linestyle of the convex hull.
  * `convex_hull_linewidth = 1` sets the width of the convex hull.
  * `ghost_edge_color = :blue` sets the color of the ghost edges.
  * `ghost_edge_linestyle = :solid` sets the linestyle of the ghost edges.
  * `ghost_edge_linewidth = 1` sets the width of the ghost edges.
  * `ghost_edge_extension_factor = 0.1` sets the extension factor for the rectangle that the exterior ghost edges are extended onto.
  * `bounding_box::Union{Automatic, Rect2, Tuple} = automatic`: Sets the bounding box for truncating ghost edges which can be a `Rect2` (or `BBox`) or a tuple of the form `(xmin, xmax, ymin, ymax)`. By default, the rectangle will be given by `[a - eΔx, b + eΔx] × [c - eΔy, d + eΔy]` where `e` is the `ghost_edge_extension_factor`, `Δx = b - a` and `Δy = d - c` are the lengths of the sides of the rectangle, and `[a, b] × [c, d]` is the bounding box of the points in the triangulation.
  * `constrained_edge_color = :magenta` sets the color of the constrained edges.
  * `constrained_edge_linestyle = :solid` sets the linestyle of the constrained edges.
  * `constrained_edge_linewidth = 1` sets the width of the constrained edges.
