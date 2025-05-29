```
lattice_plot(sol, sp, lrs::LatticeReactionSystem, filename::String; t = sol.tspan[2], kwargs...)
```

Creates a plot of a `LatticeReactionSystem` simulation. The plot is created at the time point specified by `t` (defaults to the simulation's final time point).

Arguments (all lattices):

  * `sol`: The simulation we wish to plot.
  * `sp`: The species whose values we wish to plot. Can be provided either in its symbolic form or as a symbol.
  * `lrs`: The `LatticeReactionSystem` which was simulated.
  * `t = sol.t[end]`: The time point at which we wish to plot the solution

In addition, depending on the type of lattice used, the following optional arguments might be relevant.

Arguments (1d lattices):

  * `markersize = 20`: The size of the markers marking each compartment's value.

Arguments (Graph & 2d lattices):

  * `colormap = :BuGn_7`: The colour map with which we display the species amounts in the animation.
  * `plot_min = nothing`: The minimum value for the colour scale (values less than this will be set at this value when the colour scale is computed). If `nothing`, use the simulation's minimum value (across the entire simulation, not just at the plotted time value).
  * `plot_max = nothing`: The maximum value for the colour scale (values more than this will be set at this value when the colour scale is computed). If `nothing`, use the simulation's minimum value (across the entire simulation, not just at the plotted time value).

Arguments (Graph lattices):

  * `node_size = 50`: The size of the compartments in the plot.
  * `layout = Spring()`: The layout for the graph nodes in the plot. Can be provided as a vector, where the i'th element is a 2-valued tuple (determining the i'th compartment's y and x positions, respectively).

Notes: 

  * For masked lattices, there are no value displayed for grid points which do not correspond to a compartments.
  * The current plotting interface is a work in progress, and modifications are expected. if you have any feedback, please contact the package authors.
  * Additional arguments can be passed to `lattice_plot`, which then will be passed to Makie's `lines` plotting command.
