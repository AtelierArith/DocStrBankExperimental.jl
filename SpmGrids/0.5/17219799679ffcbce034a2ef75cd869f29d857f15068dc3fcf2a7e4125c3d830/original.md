```
plot_plane(grid::SpmGrid, response_channel::String,
    x_index::GridRange, y_index::GridRange, channel_index::GridRange=:;
    bwd::Bool=false, ax::Any=nothing, backend::Module=Main,
    kwargs...)::NamedTuple
```

Plots a plane of `response_channel` in the three-dimensional data spanned by x,y plane and the sweep signal. Indexing is done through `x_index`, `y_index` and `channel_index` and should be done such that a two-dimensional array is obtained. If `bwd` is set to `true`, then data from the backward sweep is plotted if it exists.

Before using this function, a [Makie](https://makie.juliaplots.org/) backend (`GLMakie`, `CairoMakie` or `WGLMakie`) should be imported and the figure or axis should be set up. A particular Axis can be specified via the `ax` keyword argument. By default, the Makie backend from the `Main` module is used; it can also be directly specified via the `backend` keyword argument.

Extra keyword arguments can be specified and will be passed through to the plot function.

Returns a NamedTuple containing the heatmap, the colorbar label and the plot label.
