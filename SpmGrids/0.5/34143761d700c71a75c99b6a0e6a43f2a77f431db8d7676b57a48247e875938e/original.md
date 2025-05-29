plot*parameter*plane(grid::SpmGrid, parameter::String,         x*index::GridRange=:, y*index::GridRange=:;         ax::Any=nothing, backend::Module=Main,         kwargs...)::NamedTuple

Plots values of `parameters` as a function of the x,y plane Indexing is done through `x_index`, `y_index`.

Before using this function, a [Makie](https://makie.juliaplots.org/) backend (`GLMakie`, `CairoMakie` or `WGLMakie`) should be imported and the figure or axis should be set up. A particular Axis can be specified via the `ax` keyword argument. By default, the Makie backend from the `Main` module is used; it can also be directly specified via the `backend` keyword argument.

Extra keyword arguments can be specified and will be passed through to the plot function.

Returns a NamedTuple containing the heatmap, the colorbar label and the plot label.
