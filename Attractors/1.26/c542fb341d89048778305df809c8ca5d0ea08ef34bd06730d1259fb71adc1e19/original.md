```
animate_attractors_continuation(
    ds::DynamicalSystem, attractors_cont, fractions_cont, pcurve;
    kwargs...
)
```

Animate how the found system attractors and their corresponding basin fractions change as the system parameter is increased. This function combines the input and output of the [`global_continuation`](@ref) function into a video output.

The input dynamical system `ds` is used to evolve initial conditions sampled from the found attractors, so that the attractors are better visualized. `attractors_cont, fractions_cont` are the output of [`global_continuation`](@ref) while `ds, pcurve` are the input to [`global_continuation`](@ref).

## Keyword arguments

  * `savename = "attracont.mp4"`: name of video output file.
  * `framerate = 4`: framerate of video output.
  * `Δt, T`: propagated to `trajectory` for evolving an initial condition sampled from an attractor.
  * Also all [common plotting keywords](@ref common_plot_kwargs).
  * `figure, axis, fracaxis, legend`: named tuples propagated as keyword arguments to the creation of the `Figure`, the `Axis`, the "bar-like" axis containing the fractions, and the `axislegend` that adds the legend (if `add_legend = true`).
  * `add_legend = true`: whether to display the axis legend.
