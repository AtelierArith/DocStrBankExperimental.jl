```
lattice_kymograph(sol, sp, lrs::LatticeReactionSystem, kwargs...)
```

Creates a kymograph of a `LatticeReactionSystem` simulation based on a Cartesian or masked lattice.  The plot shows the compartments on the y-axis, and the time development of the system's state along the x-axis. Species amounts are shown as a heatmap.

Arguments (all lattices):

  * `sol`: The simulation we wish to plot.
  * `sp`: The species whose values we wish to plot. Can be provided either in its symbolic form or as a symbol.
  * `lrs`: The `LatticeReactionSystem` which was simulated.
  * `colormap = :BuGn_7`: The colour map with which we display the species amounts in the kymograph.
  * `nframes = 200`: The number of time samples which the time series is sampled with.
  * `plot_min = nothing`: The minimum value for the colour scale (values less than this will be set at this value when the colour scale is computed). If `nothing`, use the simulation's minimum value.
  * `plot_max = nothing`: The maximum value for the colour scale (values more than this will be set at this value when the colour scale is computed). If `nothing`, use the simulation's minimum value.

Notes: 

  * For masked lattices, there are no value displayed for grid points which do not correspond to a compartments.
  * The current plotting interface is a work in progress, and modifications are expected. if you have any feedback, please contact the package authors.
  * Additional arguments can be passed to `lattice_plot`, which then will be passed to Makie's `heatmap` plotting command.
