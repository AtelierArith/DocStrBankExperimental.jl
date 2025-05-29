```
theme_acs(; kwargs...)
```

Generate Makie theme for producing figures for ACS (American Chemical Society).

Save the figure using `savefig("path_to_figure.pdf", fig)` or `save("path_to_figure.pdf", fig, pt_per_unit=1.0)`.

# Auguments

  * `width=3.25`: width of figure in unit of inches.
  * `colors=COLORS[1]`: color palette specified by a list of colors.
  * `linestyles=LINESTYLES`: a list of line styles to be cycled.
  * `markers=MARKERS`: a list of markers to be cycled.
  * `ishollowmarkers`: a list of `true` or `false` values, which indicates whether the current marker is hollow.
  * `palette=nothing`: a palette to be used by Makie. It is a `NamedTuple` when it is not `nothing`. Example: (color=COLORS[1], marker=MARKERS). It is key will be referenced by `cycle`, `linecycle` and `scattercycle`.
  * `cycle=CYCLE`: a Makie `Cycle` instance tell how Makie will cycle figure properties.
  * `linecycle=nothing`: `Cycle` instance used by `Line` plots. If it is `nothing`, then `cycle` value will be used instead.
  * `scattercycle=nothing`: `Cycle` instance used by `Scatter` plots. If it is `nothing`, then `cycle` value will be used instead.
  * `markerstrokewidth=0`: customize the stroke width of markers.
  * `heightwidthratio=HWRATIO`: set the aspect ratio of the figure as a multiple of `width`.
  * `usetexfont=true`: set if Makie should use the ComputerModern font provided by [`MathTexEngine.jl`](https://github.com/Kolaru/MathTeXEngine.jl).

See also [`theme_aps`](@ref), [`theme_rsc`](@ref), and [`theme_web`](@ref).
