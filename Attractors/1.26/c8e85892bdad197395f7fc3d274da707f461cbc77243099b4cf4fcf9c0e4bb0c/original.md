```
plot_basins_attractors_curves(
    fractions_cont, attractors_cont, a2rs [, prange]
    kwargs...
)
```

Convenience combination of [`plot_basins_curves`](@ref) and [`plot_attractors_curves`](@ref) in a multi-panel plot that shares legend, colors, markers, etc. This function allows `a2rs` to be a `Vector` of functions, each mapping attractors into real numbers. Below the basins fractions plot, one additional panel is created for each entry in `a2rs`. `a2rs` can also be a single function, in which case only one panel is made.
