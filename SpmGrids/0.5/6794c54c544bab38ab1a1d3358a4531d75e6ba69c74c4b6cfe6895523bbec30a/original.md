```
plot_line(grid::SpmGrid, response_channel::String,
    x_index::GridRange, y_index::GridRange, channel_index::GridRange=nothing;
    sweep_channel::String="", bwd::Bool=true, ax::Any=nothing, backend::Module=Main,
    kwargs...)::NamedTuple
```

Plots the `response_channel` along a line in the three-dimensional data spanned by x,y plane and the spectroscopy data. Indexing is done through `x_index`, `y_index` and `channel_index` and should be done such that a one-dimensional array is obtained. It is also possible to plot `response_channel` vs `sweep_channel` (which defaults to the sweep signal if not specified) for one point in the grid If `bwd` is `true` (default), the plot will include data from backward sweep as well (if they exist).

Before using this function, a [Makie](https://makie.juliaplots.org/) backend (`GLMakie`, `CairoMakie` or `WGLMakie`) should be imported and the figure or axis should be set up. A particular Axis can be specified via the `ax` keyword argument. By default, the Makie backend from the `Main` module is used; it can also be directly specified via the `backend` keyword argument.

Extra keyword arguments can be specified and will be passed through to the plot function. Keyword arrguments with the suffix `_bwd` will be used for plotting of the backward scan.    

Returns a NamedTuple.
