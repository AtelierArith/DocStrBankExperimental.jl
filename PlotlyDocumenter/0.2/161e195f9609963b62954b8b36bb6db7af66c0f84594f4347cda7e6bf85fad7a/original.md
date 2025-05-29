```
PlotlyDocumenterPlot
```

A wrapper type for Plotly plot data that enables flexible rendering in different contexts.

The plot data is stored as strings containing the JSON representation of the plot's data, layout and config.

The `options` field contains rendering options that control how the plot is displayed. For the default  `text/html` MIME output, see [`to_documenter`](@ref) for more information.
