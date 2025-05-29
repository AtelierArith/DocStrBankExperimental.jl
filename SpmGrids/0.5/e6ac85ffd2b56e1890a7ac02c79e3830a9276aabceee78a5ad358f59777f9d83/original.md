```
interactive_display(grid::SpmGrid, response_channel::String="", response_channel2::String="", parameter::String="";
    bwd::Bool=false, fig::Any=nothing, backend::Module=Main)::Any
```

Display the grid in an interactive GUI that can be used in Pluto, Jupyter, or other interactive environments. `response_channel` specifies the initial choice of the response channel, `response_channel2` specifies the initial choice of the response channel for the second line plot, `parameter` specifies the initial parameter to plot.

Before using this function, a [Makie](https://makie.juliaplots.org/) backend (`GLMakie`, `CairoMakie` or `WGLMakie`) should be imported and the figure can be set up and passed via the `fig` keyword argument.
