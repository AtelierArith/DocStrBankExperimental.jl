```
function plotly(p::Symbol; layout = Symbol(p, ".layout"), config = Symbol(p, ".config"), configtype = default_config_type(), keepselection = false, kwargs...)
```

This is a convenience function for rendering a PlotlyBase.Plot or a struct with fields data, layout and config

# Example

```julia
julia> plotly(:plot)
"<plotly :data="plot.data" :layout="plot.layout" :config="plot.config"></plotly>"
```

For multiple plots with a common config or layout a typical usage is

```julia
julia> plotly(:plot, config = :config)
"<plotly :data="plot.data" :layout="plot.layout" :config="config"></plotly>"
```
