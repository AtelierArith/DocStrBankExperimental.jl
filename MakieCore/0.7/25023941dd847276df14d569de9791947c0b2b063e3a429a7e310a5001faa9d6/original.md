```
scatter(positions)
scatter(x, y)
scatter(x, y, z)
```

Plots a marker for each element in `(x, y, z)`, `(x, y)`, or `positions`.

## Attributes

### Specific to `Scatter`

  * `color=theme(scene, :markercolor)` sets the color of the marker. If no color is set, multiple calls to `scatter!` will cycle through the axis color palette. Otherwise, one can set one color per point by passing a `Vector{<:Colorant}`, or one colorant for the whole scatterplot. If color is a vector of numbers, the colormap args are used to map the numbers to colors.
  * `cycle::Vector{Symbol} = [:color]` sets which attributes to cycle when creating multiple plots.
  * `marker::Union{Symbol, Char, Matrix{<:Colorant}, BezierPath, Polygon}` sets the scatter marker.
  * `markersize::Union{<:Real, Vec2f} = 9` sets the size of the marker.
  * `markerspace::Symbol = :pixel` sets the space in which `markersize` is given. See `Makie.spaces()` for possible inputs.
  * `strokewidth::Real = 0` sets the width of the outline around a marker.
  * `strokecolor::Union{Symbol, <:Colorant} = :black` sets the color of the outline around a marker.
  * `glowwidth::Real = 0` sets the size of a glow effect around the marker.
  * `glowcolor::Union{Symbol, <:Colorant} = (:black, 0)` sets the color of the glow effect.
  * `rotations::Union{Real, Billboard, Quaternion} = Billboard(0f0)` sets the rotation of the marker. A `Billboard` rotation is always around the depth axis.
  * `transform_marker::Bool = false` controls whether the model matrix (without translation) applies to the marker itself, rather than just the positions. (If this is true, `scale!` and `rotate!` will affect the marker.)

### Color attributes

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` sets the colormap that is sampled for numeric `color`s. `PlotUtils.cgrad(...)`, `Makie.Reverse(any_colormap)` can be used as well, or any symbol from ColorBrewer or PlotUtils. To see all available color gradients, you can call `Makie.available_gradients()`.
  * `colorscale::Function = identity` color transform function. Can be any function, but only works well together with `Colorbar` for `identity`, `log`, `log2`, `log10`, `sqrt`, `logit`, `Makie.pseudolog10` and `Makie.Symlog10`.
  * `colorrange::Tuple{<:Real, <:Real}` sets the values representing the start and end points of `colormap`.
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)` sets a replacement color for `color = NaN`.
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing` sets a color for any value below the colorrange.
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing` sets a color for any value above the colorrange.
  * `alpha = 1.0` sets the alpha value of the colormap or color attribute. Multiple alphas like in `plot(alpha=0.2, color=(:red, 0.5)`, will get multiplied.

### Generic attributes

  * `visible::Bool = true` sets whether the plot will be rendered or not.
  * `overdraw::Bool = false` sets whether the plot will draw over other plots. This specifically means ignoring depth checks in GL backends.
  * `transparency::Bool = false` adjusts how the plot deals with transparency. In GLMakie `transparency = true` results in using Order Independent Transparency.
  * `fxaa::Bool = true` adjusts whether the plot is rendered with fxaa (anti-aliasing).
  * `inspectable::Bool = true` sets whether this plot should be seen by `DataInspector`.
  * `depth_shift::Float32 = 0f0` adjusts the depth value of a plot after all other transformations, i.e. in clip space, where `0 <= depth <= 1`. This only applies to GLMakie and WGLMakie and can be used to adjust render order (like a tunable overdraw).
  * `model::Makie.Mat4f` sets a model matrix for the plot. This replaces adjustments made with `translate!`, `rotate!` and `scale!`.
  * `space::Symbol = :data` sets the transformation space for box encompassing the volume plot. See `Makie.spaces()` for possible inputs.
