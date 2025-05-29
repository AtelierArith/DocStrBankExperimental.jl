```
plotly_plot(args...;kwargs...)
```

This function will forward args... and kwargs... to the relevant `plot` function of the loaded Plotly packages, based on the priority specified in `PlotlyExtensionHelper.PLOT_FUNC_PRIORITY`.

It is intended to be used inside extensions to produce output of plotting function based on one of the supported Plotly based packages (i.e. PlotlyBase, PlotlyJS or PlutoPlotly)
