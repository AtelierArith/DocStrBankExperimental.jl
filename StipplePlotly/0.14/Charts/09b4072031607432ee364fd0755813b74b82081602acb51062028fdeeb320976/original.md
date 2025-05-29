```
function watchplots(model = "this"; observe = true, parentSelector::Union{Nothing, AbstractString} = nothing)
```

Generates a js script that forwards plotly events, e.g. point selection or hovering, to their respective model fields. `model` can be a string, a model or a model type. Dynamically added plots are also covered.

The recommended usage is to called it on the mounted event. In that case the model argument can be omitted. `Stipple.js_mounted(::Example) = watchplots()`

Plots to be covered by this approach must contain at least one class entry `'sync_[prefix]'`, e.g `sync_plot`. You can use the keyword arguments `syncevents` or `syncprefix` of `plot()` to generate the UI plot nodes:

```
julia> plot("plot.data", syncevents = true)
"<plotly :data="plot.data" :layout="{}" class="sync_plot"></plotly>"

julia> plot("plot.data", syncprefix = "plot1")
"<plotly :data="plot.data" :layout="{}" class="sync_plot1"></plotly>"
```

# Example

```julia
@vars Example begin
    plot::R{Plot} = Plot()
    plot_selected::R{Dict{String, Any}} = Dict{String, Any}()
    plot_hover::R{Dict{String, Any}} = Dict{String, Any}()
    plot1_selected::R{Dict{String, Any}} = Dict{String, Any}()
end

function ui(model::Example)
    page(model, class = "container",
    row(cell(class = "st-module", id = "plotcontainer", [
      # syncs plotly events to field plot_selected, plot_hover, etc...
      plotly(:plot, syncevents = true),

      # syncs plotly events to field plot1_selected, plot1_hover, etc...
      plotly(:plot, syncprefix = "plot1", @iif(length(model.plot.data) > 0)),
    ])))
end

Stipple.js_mounted(::Example) = watchplots()

function handlers(model)
  on(model.isready) do isready
      isready || return
      push!(model)
  end

  on(model.plot_selected) do data
      haskey(data, "points") && @info "Selection: $(getindex.(data["points"], "pointIndex"))"
  end

  return model
end
```
