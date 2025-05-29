```
VisualizationCallback(; interval=0,
                        solution_variables=cons2prim,
                        variable_names=[],
                        show_mesh=false,
                        plot_data_creator=PlotData2D,
                        plot_creator=show_plot,
                        plot_arguments...)
```

Create a callback that visualizes results during a simulation, also known as *in-situ visualization*.

!!! warning "Experimental implementation"
    This is an experimental feature and may change in any future releases.


The `interval` specifies the number of time step iterations after which a new plot is generated. The available variables to plot are configured with the `solution_variables` parameter, which acts the same way as for the [`SaveSolutionCallback`](@ref). The variables to be actually plotted can be selected by providing a single string or a list of strings to `variable_names`, and if `show_mesh` is `true`, an additional plot with the mesh will be generated.

To customize the generated figure, `plot_data_creator` allows to use different plot data types. With `plot_creator` you can further specify an own function to visualize results, which must support the same interface as the default implementation [`show_plot`](@ref). All remaining keyword arguments are collected and passed as additional arguments to the plotting command.
