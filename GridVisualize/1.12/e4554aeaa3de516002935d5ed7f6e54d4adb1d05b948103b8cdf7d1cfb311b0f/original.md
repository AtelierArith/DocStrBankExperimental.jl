```julia
GridVisualizer(
;
    Plotter,
    kwargs...
) -> GridVisualize.GridVisualizer

```

Create a  grid visualizer

Plotter: defaults to `default_plotter()` and can be `PyPlot`, `Plots`, `VTKView`, `Makie` or `PlutoVista´. This pattern allows  to pass the backend as a module to a plot function without heavy default package dependencies.

Depending on the `layout` keyword argument, a 2D grid of subplots is created. Further `...plot!` commands then plot into one of these subplots:

```julia
vis=GridVisualizer(Plotter=PyPlot, layout=(2,2)
...plot!(vis[1,2], ...)
```

A `...plot`  command just implicitly creates a plot context:

```julia
gridplot(grid, Plotter=PyPlot) 
```

is equivalent to

```julia
vis=GridVisualizer(Plotter=PyPlot, layout=(1,1))
gridplot!(vis,grid) 
reveal(vis)
```

Please note that the return values of all plot commands are specific to the Plotter.

An interactive mode switch key   for GLMakie (`,`)  and  VTKView (`*`) allows to toggle between "gallery view" showing all plots at once and "focused view" showing only one plot.

Keyword arguments: see [`available_kwargs`](@ref)
