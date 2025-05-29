```
voronoiplot(x, y, values; kwargs...)
voronoiplot(values; kwargs...)
voronoiplot(x, y; kwargs...)
voronoiplot(positions; kwargs...)
voronoiplot(vorn::VoronoiTessellation; kwargs...)
```

Generates and plots a Voronoi tessalation from `heatmap`- or point-like data. The tessellation can also be passed directly as a `VoronoiTessellation` from DelaunayTriangulation.jl.

## Attributes

  * `show_generators = true` determines whether to plot the individual generators.
  * `markersize = 12` sets the size of the points.
  * `marker = :circle` sets the shape of the points.
  * `markercolor = :black` sets the color of the points.
  * `strokecolor = :black` sets the strokecolor of the polygons.
  * `strokewidth = 1` sets the width of the polygon stroke.
  * `color = automatic` sets the color of the polygons. If `automatic`, the polygons will be individually colored according to the colormap.
  * `unbounded_edge_extension_factor = 0.1` sets the extension factor for the unbounded edges, used in `DelaunayTriangulation.polygon_bounds`.
  * `clip::Union{Automatic, Rect2, Circle, Tuple} = automatic` sets the clipping area for the generated polygons which can be a `Rect2` (or `BBox`), `Tuple` with entries `(xmin, xmax, ymin, ymax)` or as a `Circle`. Anything outside the specified area will be removed. If the `clip` is not set it is automatically determined using `unbounded_edge_extension_factor` as a `Rect`.

### Color attributes

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` sets the colormap that is sampled for numeric `color`s. `PlotUtils.cgrad(...)`, `Makie.Reverse(any_colormap)` can be used as well, or any symbol from ColorBrewer or PlotUtils. To see all available color gradients, you can call `Makie.available_gradients()`.
  * `colorscale::Function = identity` color transform function. Can be any function, but only works well together with `Colorbar` for `identity`, `log`, `log2`, `log10`, `sqrt`, `logit`, `Makie.pseudolog10` and `Makie.Symlog10`.
  * `colorrange::Tuple{<:Real, <:Real}` sets the values representing the start and end points of `colormap`.
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)` sets a replacement color for `color = NaN`.
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing` sets a color for any value below the colorrange.
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing` sets a color for any value above the colorrange.
  * `alpha = 1.0` sets the alpha value of the colormap or color attribute. Multiple alphas like in `plot(alpha=0.2, color=(:red, 0.5)`, will get multiplied.
