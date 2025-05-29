```
plot(data::Union{Symbol,AbstractString}, args...;
  layout::Union{Symbol,AbstractString,LayoutType} = Charts.PlotLayout(),
  config::Union{Symbol,AbstractString,Nothing,ConfigType} = nothing, configtype = Charts.PlotConfig,
  syncevents::Bool = false, syncprefix = "", class = "", keepselection::Bool = false, kwargs...) :: String  where {LayoutType, ConfigType}
```

Generate a plotly plot with the given data and arguments. Parameters:

  * `data::Union{Symbol,AbstractString}`: name of the field that holds the plot data
  * `layout::Union{Symbol,AbstractString,LayoutType}`: The layout of the plot. Default: `Charts.PlotLayout()`
  * `config::Union{Symbol,AbstractString,Nothing,ConfigType}`: The configuration of the plot. Default: `nothing`
  * `configtype::ConfigType`: The type of the configuration. Default: `Charts.PlotConfig`
  * `syncevents::Bool`: Whether to sync events. Default: `false`
  * `syncprefix::String`: Syncing is controlled via the class attribute of the plot. If left empty, the class is derived from the data name.
  * `class::String`: additional class attribute for the plot
  * `args`: further custom arguments
  * `kwargs`: further custom keyword arguments

Forwarding plotly events is achieved by setting `syncevents` to `true` or by providing a `syncprefix`. Model fields that the events are forwarded to are derived from the `syncprefix` and the event type, e.g. `syncprefix = "myplot"` will forward the `plotly_selected` event to the `myplot_selected` model field. The most common event types are `plotly_selected`, `plotly_hover`, `plotly_click`, and `plotly_relayout`, which can be included in the model via `@mixin myplot::PBPlotWithEvents`.

An example of event forwarding can be found in the docstring of StipplePlotly.
