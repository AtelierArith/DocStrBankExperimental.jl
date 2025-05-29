```
lattice_animation(sol, sp, lrs::LatticeReactionSystem, filename::String; kwargs...)
```

Creates an animation of a `LatticeReactionSystem` simulation. The animation is saved to a file,  whose name is provided in the `filename` argument.

Arguments (all lattices):

  * `sol`: The simulation we wish to animate.
  * `sp`: The species which values we wish to animate. Can be provided either in its symbolic form or as a symbol.
  * `lrs`: The `LatticeReactionSystem` which was simulated.
  * `filename`: The name of the file to which we wish to save the animation.
  * `nframes = 200`: The number of frames in the animation (these are evenly samples across the simulation).
  * `framerate = 20`: The frame rate of the animation.
  * `ttitle = true`: Whether to add a title showing the simulation's time throughout the animation.

In addition, depending on the type of lattice used, the following optional arguments might be relevant.

Arguments (1d lattices):

  * `markersize = 20`: The size of the markers marking each compartment's value.
  * `plot_min = nothing`: The y-scale's minimum. If `nothing`, use the simulation's minimum value.
  * `plot_max = nothing`: The y-scale's maximum. If `nothing`, use the simulation's maximum value.

Arguments (Graph & 2d lattices):

  * `colormap = :BuGn_7`: The colour map with which we display the species amounts in the animation.
  * `plot_min = nothing`: The minimum value for the colour scale (values less than this will be set at this value when the colour scale is computed). If `nothing`, use the simulation's minimum value.
  * `plot_max = nothing`: The maximum value for the colour scale (values more than this will be set at this value when the colour scale is computed). If `nothing`, use the simulation's minimum value.

Arguments (Graph lattices):

  * `node_size = 50`: The size of the compartments in the plot.
  * `layout = Spring()`: The layout for the graph nodes in the plot. Can be provided as a vector, where the i'th element is a 2-valued tuple (determining the i'th compartment's y and x positions, respectively).

Notes: 

  * For masked lattices, there are no value displayed for grid points which do not correspond to a compartments.
  * The current animation interface if a work in progress, and modifications are expected. if you have any feedback, please contact the package authors.
  * Additional arguments can be passed to `lattice_animation`, which then will be passed to Makie's `heatmap` plotting command.
