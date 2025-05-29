```
plot_erpimage!(f::Union{GridPosition, GridLayout, Figure}, data::AbstractMatrix{Float64}; kwargs...)
plot_erpimage!(f::Union{GridPosition, GridLayout, Figure}, data::Observable{<:AbstractMatrix}; kwargs...)
plot_erpimage!(f::Union{GridPosition, GridLayout, Figure}, times::Observable{<:AbstractVector}, data::Observable{<:AbstractMatrix{<:Real}}; kwargs...)

plot_erpimage(times::AbstractVector, data::Union{<:Observable{Matrix{<:Real}}, Matrix{<:Real}}; kwargs...)
plot_erpimage(data::Matrix{Float64}; kwargs...)
```

Plot an ERP image.

## Arguments:

  * `f::Union{GridPosition, GridLayout, Figure}`
      `Figure`, `GridLayout`, or `GridPosition` to draw the plot.
  * `data::Union{DataFrame, Vector{Float32}}`
      Data for the plot visualization.

## Keyword arguments (kwargs)

  * `erpblur::Number = 10`
      Number indicating how much blur is applied to the image. 
      Gaussian blur of the `ImageFiltering` module is used.
      Non-Positive values deactivate the blur.
  * `sortvalues::Vector{Int64} = false`
      Parameter over which plot will be sorted. Using `sortperm()` of Base Julia.
      `sortperm()` computes a permutation of the array's indices that puts the array in sorted order.
  * `sortindex::Vector{Int64} = nothing`
      Sorting over index values.
  * `meanplot::bool = false`
      Add a line plot below the ERP image, showing the mean of the data.
  * `show_sortval::bool = false`
      Add a plot on the right from ERP image, showing the distribution of the sorting data.
  * `sortval_xlabel::String = "Sorting variable"`
      If `show_sortval = true` controls xlabel.
  * `axis.ylabel::String = "Trials"`
      If `sortvalues = true` the default text will change to "Sorted trials", but it could be changed to any values specified manually.
  * `meanplot_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of meanplot.
      To see all options just type `?Axis` in REPL.
      Defaults: (height = 100, xlabel = "Time", xlabelpadding = 0, xautolimitmargin = (0, 0))
  * `sortplot_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of meanplot.
      To see all options just type `?Axis` in REPL.
      Defaults: (ylabelvisible = true, yticklabelsvisible = false)

## Shared plot configuration options

The shared plot options can be used as follows: `type = (; key = value, ...))`.
For example, `plot_x(...; colorbar = (; vertical = true, label = "Test"))`.
Multiple defaults will be cycled until match.

Placing `;` is important!

**figure =** NamedTuple() - *use `kwargs...` of [`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)* 

**axis =** (xlabel = "Time", ylabel = "Trials") - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = true, use_colorbar = true) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = Makie.Reverse{String}("RdBu"),) - *use `kwargs...` of [`Makie.heatmap`](https://docs.makie.org/stable/reference/plots/heatmap/)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, label = "Voltage [µV]") - *use `kwargs...` of  [`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)* 

**Return Value:** `Figure` displaying the ERP image. 
