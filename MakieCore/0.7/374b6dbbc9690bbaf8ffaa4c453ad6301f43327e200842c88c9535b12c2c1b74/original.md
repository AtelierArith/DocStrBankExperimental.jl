```
poly(vertices, indices; kwargs...)
poly(points; kwargs...)
poly(shape; kwargs...)
poly(mesh; kwargs...)
```

Plots a polygon based on the arguments given. When vertices and indices are given, it functions similarly to `mesh`. When points are given, it draws one polygon that connects all the points in order. When a shape is given (essentially anything decomposable by `GeometryBasics`), it will plot `decompose(shape)`.

```
poly(coordinates, connectivity; kwargs...)
```

Plots polygons, which are defined by `coordinates` (the coordinates of the vertices) and `connectivity` (the edges between the vertices).

## Attributes

### Specific to `Poly`

  * `color=theme(scene, :patchcolor)` sets the color of the poly. Can be a `Vector{<:Colorant}` for per vertex colors or a single `Colorant`.  A `Matrix{<:Colorant}` can be used to color the mesh with a texture, which requires the mesh to contain texture coordinates.  Vector or Matrices of numbers can be used as well, which will use the colormap arguments to map the numbers to colors.  One can also use `Makie.LinePattern`, to cover the poly with a regular stroke pattern.
  * `strokecolor::Union{Symbol, <:Colorant} = :black` sets the color of the outline around a marker.
  * `strokecolormap`::Union{Symbol, Vector{<:Colorant}} = :viridis`sets the colormap that is sampled for numeric`color`s.
  * `strokewidth::Real = 0` sets the width of the outline around a marker.
  * `linestyle::Union{Nothing, Symbol, Vector} = nothing` sets the pattern of the line (e.g. `:solid`, `:dot`, `:dashdot`)

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
