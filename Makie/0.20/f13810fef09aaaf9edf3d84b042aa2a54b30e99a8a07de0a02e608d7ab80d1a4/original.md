```
tricontourf(triangles::Triangulation, zs; kwargs...)
tricontourf(xs, ys, zs; kwargs...)
```

Plots a filled tricontour of the height information in `zs` at the horizontal positions `xs` and vertical positions `ys`. A `Triangulation` from DelaunayTriangulation.jl can also be provided instead of `xs` and `ys` for specifying the triangles, otherwise an unconstrained triangulation of `xs` and `ys` is computed.

## Attributes

### Specific to `Tricontourf`

  * `levels = 10` can be either an `Int` which results in n bands delimited by n+1 equally spaced levels, or it can be an `AbstractVector{<:Real}` that lists n consecutive edges from low to high, which result in n-1 bands.
  * `mode = :normal` sets the way in which a vector of levels is interpreted, if it's set to `:relative`, each number is interpreted as a fraction between the minimum and maximum values of `zs`. For example, `levels = 0.1:0.1:1.0` would exclude the lower 10% of data.
  * `extendlow = nothing`. This sets the color of an optional additional band from `minimum(zs)` to the lowest value in `levels`. If it's `:auto`, the lower end of the colormap is picked and the remaining colors are shifted accordingly. If it's any color representation, this color is used. If it's `nothing`, no band is added.
  * `extendhigh = nothing`. This sets the color of an optional additional band from the highest value of `levels` to `maximum(zs)`. If it's `:auto`, the high end of the colormap is picked and the remaining colors are shifted accordingly. If it's any color representation, this color is used. If it's `nothing`, no band is added.
  * `triangulation = DelaunayTriangulation()`. The mode with which the points in `xs` and `ys` are triangulated. Passing `DelaunayTriangulation()` performs a Delaunay triangulation. You can also pass a preexisting triangulation as an `AbstractMatrix{<:Int}` with size (3, n), where each column specifies the vertex indices of one triangle, or as a `Triangulation` from DelaunayTriangulation.jl.

### Generic

  * `visible::Bool = true` sets whether the plot will be rendered or not.
  * `overdraw::Bool = false` sets whether the plot will draw over other plots. This specifically means ignoring depth checks in GL backends.
  * `transparency::Bool = false` adjusts how the plot deals with transparency. In GLMakie `transparency = true` results in using Order Independent Transparency.
  * `fxaa::Bool = false` adjusts whether the plot is rendered with fxaa (anti-aliasing).
  * `inspectable::Bool = true` sets whether this plot should be seen by `DataInspector`.
  * `depth_shift::Float32 = 0f0` adjusts the depth value of a plot after all other transformations, i.e. in clip space, where `0 <= depth <= 1`. This only applies to GLMakie and WGLMakie and can be used to adjust render order (like a tunable overdraw).
  * `model::Makie.Mat4f` sets a model matrix for the plot. This replaces adjustments made with `translate!`, `rotate!` and `scale!`.
  * `color` sets the color of the plot. It can be given as a named color `Symbol` or a `Colors.Colorant`. Transparency can be included either directly as an alpha value in the `Colorant` or as an additional float in a tuple `(color, alpha)`. The color can also be set for each scattered marker by passing a `Vector` of colors or be used to index the `colormap` by passing a `Real` number or `Vector{<: Real}`.
  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` sets the colormap from which the band colors are sampled.
  * `colorscale::Function = identity` color transform function.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.tricontourf}` are: 

```
  colormap       :viridis
  colorscale     identity
  edges          "nothing"
  extendhigh     "nothing"
  extendlow      "nothing"
  inspectable    true
  levels         10
  mode           :normal
  nan_color      :transparent
  transparency   false
  triangulation  Makie.DelaunayTriangulation()
```
