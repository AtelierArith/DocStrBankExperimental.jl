```
plot_attractors_curves(attractors_cont, attractor_to_real [, prange]; kw...)
```

Same as in [`plot_basins_curves`](@ref) but visualize the attractor dependence on the parameter(s) instead of their basin fraction. The function `attractor_to_real` takes as input a `StateSpaceSet` (attractor) and returns a real number so that it can be plotted versus the parameter axis. See also [`plot_basins_attractors_curves`](@ref).

Same keywords as [`plot_continuation_curves`](@ref).
