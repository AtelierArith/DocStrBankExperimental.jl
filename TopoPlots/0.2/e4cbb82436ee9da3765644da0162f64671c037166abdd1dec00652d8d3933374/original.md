```
topoplot(data::Vector{<:Real}, positions::Vector{<: Point2})
```

Creates an irregular interpolation for each `data[i]` point at `positions[i]`.

# Attributes

  * `colormap = Reverse(:RdBu)`
  * `colorrange = automatic`
  * `labels::Vector{<:String}` = nothing: names for each data point
  * `interpolation::Interpolator = CloughTocher()`: Applicable interpolators are TopoPlots.CloughTocher, TopoPlots.DelaunayMesh, TopoPlots.NaturalNeighboursMethod, TopoPlots.NullInterpolator, TopoPlots.ScatteredInterpolationMethod, TopoPlots.SplineInterpolator
  * `extrapolation = GeomExtrapolation()`: Extrapolation method for adding additional points to get less border artifacts
  * `bounding_geometry = Circle`: A geometry that defines what to mask and the x/y extend of the interpolation. E.g. `Rect(0, 0, 100, 200)`, will create a `heatmap(0..100, 0..200, ...)`. By default, a circle enclosing the `positions` points will be used.
  * `enlarge` = 1.2`, enlarges the area that is being drawn. E.g., if`bounding_geometry`is`Circle`, a circle will be fitted to the points and the interpolation area that gets drawn will be 1.2x that bounding circle.
  * `interp_resolution = (512, 512)`: resolution of the interpolation
  * `label_text = false`:

      * true: add text plot for each position from `labels`
      * NamedTuple: Attributes get passed to the Makie.text! call.
  * `label_scatter = false`:

      * true: add point for each position with default attributes
      * NamedTuple: Attributes get passed to the Makie.scatter! call.
  * `markersize = 5`: size of the points defined by positions, shortcut for label_scatter=(markersize=5,)
  * `plotfnc! = heatmap!`: function to use for plotting the interpolation
  * `plotfnc_kwargs_names = [:colorrange, :colormap, :interpolate]`: different `plotfnc` support different kwargs, this array contains the keys to filter the full list which is [:colorrange, :colormap, :interpolate]
  * `contours = false`:

      * true: add scatter point for each position
      * NamedTuple: Attributes get passed to the Makie.contour! call.

# Example

```julia
using TopoPlots, CairoMakie
topoplot(rand(10), rand(Point2f, 10); contours=(color=:red, linewidth=2))
```
