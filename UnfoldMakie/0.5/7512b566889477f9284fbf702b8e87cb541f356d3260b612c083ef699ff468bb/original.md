```
plot_erp!(f::Union{GridPosition, GridLayout, Figure}, plot_data::Union{DataFrame, AbstractMatrix, AbstractVector{<:Number}}; kwargs...)
plot_erp(times, plot_data::Union{DataFrame, AbstractMatrix, AbstractVector{<:Number}}; kwargs...)
```

Plot an ERP plot.   

## Arguments

  * `f::Union{GridPosition, GridLayout, Figure}`
      `Figure`, `GridLayout`, or `GridPosition` to draw the plot.
  * `data::Union{Union{DataFrame, AbstractMatrix, AbstractVector{<:Number}, Vector{Float32}}`
      Data for the ERP plot visualization.
  * `kwargs...`
      Additional styling behavior. 
      Often used as: `plot_erp(df; mapping = (; color = :coefname, col = :conditionA))`.

## Keyword arguments (kwargs)

  * `stderror::Bool = false`
      Add an error ribbon, with lower and upper limits based on the `:stderror` column.
  * `significance::DataFrame = nothing`
      Show significant time periods as horizontal bars.
      Example: `DataFrame(from = [0.1, 0.3], to = [0.5, 0.7], coefname = ["(Intercept)", "condition: face"])`.
      If `coefname` is not specified, the significance lines will be black.
  * `layout.use_colorbar = true`
      Enable or disable colorbar.
  * `layout.use_legend = true`
      Enable or disable legend.
  * `layout.show_legend = true`
      Enable or disable legend and colorbar.
  * `mapping = (;)`
      Specify `color`, `col` (column), `linestyle`, `group`.
      F.i. `mapping = (; col = :group)` will make a column for each group.
  * `visual = (; color = Makie.wong_colors, colormap = :roma)`
      For categorical color use `visual.color`, for continuous - `visual.colormap`.

## Shared plot configuration options

The shared plot options can be used as follows: `type = (; key = value, ...))`.
For example, `plot_x(...; colorbar = (; vertical = true, label = "Test"))`.
Multiple defaults will be cycled until match.

Placing `;` is important!

**figure =** NamedTuple() - *use `kwargs...` of [`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)* 

**axis =** (xlabel = "Time", ylabel = "Voltage [µV]", yticklabelsize = 14, xtickformat = "{:.1f}") - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = true, use_colorbar = true, use_legend = true, hidespines = (:r, :t), hidedecorations = Dict{Symbol, Bool}(:grid => 1, :label => 0, :ticks => 0, :ticklabels => 0)) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y), color = (:color, :coefname, nothing)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = :roma, color = ColorTypes.RGBA{Float32}[RGBA(0.0, 0.44705883, 0.69803923, 1.0), RGBA(0.9019608, 0.62352943, 0.0, 1.0), RGBA(0.0, 0.61960787, 0.4509804, 1.0), RGBA(0.8, 0.4745098, 0.654902, 1.0), RGBA(0.3372549, 0.7058824, 0.9137255, 1.0), RGBA(0.8352941, 0.36862746, 0.0, 1.0), RGBA(0.9411765, 0.89411765, 0.25882354, 1.0)]) - *use `kwargs...` of [`Makie.lines`](https://docs.makie.org/stable/reference/plots/lines/)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center, framevisible = false) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, label = "", flipaxis = true) - *use `kwargs...` of  [`AlgebraOfGraphics.colorbar!`](@ref)* 

**Return Value:** `Figure` displaying the ERP plot.
