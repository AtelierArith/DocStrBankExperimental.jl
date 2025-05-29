```
plot_spectrum(grid::SpmGrid, sweep_channel::String, response_channel::String,
    x_index::GridRange, y_index::GridRange, channel_index::GridRange=:;
    bwd::Bool=true, ax::Any=nothing, backend::Module=Main,
    kwargs...)::NamedTuple
```

Plots a line plot of `response_channel` vs `sweep_channel` on the given `x_index` and `y_index`. If `sweep_channel` is `""`, then the sweep signal will be used for `sweep_channel`. Additionally, the spectrum data can be indexed by `channel_index`. If `bwd` is `true` (default), the plot will include data from backward sweep as well (if they exist).

Before using this function, a [Makie](https://makie.juliaplots.org/) backend (`GLMakie`, `CairoMakie` or `WGLMakie`) should be imported and the figure or axis should be set up. A particular Axis can be specified via the `ax` keyword argument. By default, the Makie backend from the `Main` module is used; it can also be directly specified via the `backend` keyword argument.

Extra keyword arguments can be specified and will be passed through to the plot function. Keyword arrguments with the suffix `_bwd` will be used for plotting of the backward scan.

Returns a NamedTuple.
