```
voronoiplot(x, y, values; kwargs...)
voronoiplot(values; kwargs...)
voronoiplot(x, y; kwargs...)
voronoiplot(positions; kwargs...)
voronoiplot(vorn::VoronoiTessellation; kwargs...)
```

Generates and plots a Voronoi tessalation from `heatmap`- or point-like data. The tessellation can also be passed directly as a `VoronoiTessellation` from DelaunayTriangulation.jl.

## Plot type

The plot type alias for the `voronoiplot` function is `Voronoiplot`.

## Attributes

**`alpha`** =  `1.0`  — The alpha value of the colormap or color attribute. Multiple alphas like in `plot(alpha=0.2, color=(:red, 0.5)`, will get multiplied.

**`clip`** =  `automatic`  — Sets the clipping area for the generated polygons which can be a `Rect2` (or `BBox`), `Tuple` with entries `(xmin, xmax, ymin, ymax)` or as a `Circle`. Anything outside the specified area will be removed. If the `clip` is not set it is automatically determined using `unbounded_edge_extension_factor` as a `Rect`.

**`color`** =  `automatic`  — Sets the color of the polygons. If `automatic`, the polygons will be individually colored according to the colormap.

**`colormap`** =  `@inherit colormap :viridis`  — Sets the colormap that is sampled for numeric `color`s. `PlotUtils.cgrad(...)`, `Makie.Reverse(any_colormap)` can be used as well, or any symbol from ColorBrewer or PlotUtils. To see all available color gradients, you can call `Makie.available_gradients()`.

**`colorrange`** =  `automatic`  — The values representing the start and end points of `colormap`.

**`colorscale`** =  `identity`  — The color transform function. Can be any function, but only works well together with `Colorbar` for `identity`, `log`, `log2`, `log10`, `sqrt`, `logit`, `Makie.pseudolog10` and `Makie.Symlog10`.

**`highclip`** =  `automatic`  — The color for any value above the colorrange.

**`lowclip`** =  `automatic`  — The color for any value below the colorrange.

**`marker`** =  `@inherit marker`  — Sets the shape of the points.

**`markercolor`** =  `@inherit markercolor`  — Sets the color of the points.

**`markersize`** =  `@inherit markersize`  — Sets the size of the points.

**`nan_color`** =  `:transparent`  — The color for NaN values.

**`show_generators`** =  `true`  — Determines whether to plot the individual generators.

**`smooth`** =  `false`  — *No docs available.*

**`strokecolor`** =  `@inherit patchstrokecolor`  — Sets the strokecolor of the polygons.

**`strokewidth`** =  `1.0`  — Sets the width of the polygon stroke.

**`unbounded_edge_extension_factor`** =  `0.1`  — Sets the extension factor for the unbounded edges, used in `DelaunayTriangulation.polygon_bounds`.
