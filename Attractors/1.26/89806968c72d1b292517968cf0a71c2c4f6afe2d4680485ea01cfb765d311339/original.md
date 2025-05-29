```
plot_continuation_curves(continuation_info [, prange]; kwargs...)
```

Same as in [`plot_basins_curves`](@ref) but visualize any arbitrary quantity characterizing the continuation. Hence, the `continuation_info` is of exactly the same format as `fractions_cont`: a vector of dictionaries, each dictionary mapping attractor IDs to real numbers. `continuation_info` is meant to accompany `attractors_cont` in [`plot_attractors_curves`](@ref).

To produce `continuation_info` from `attractors_cont` you can do something like:

```julia
continuation_info = map(attractors_cont) do attractors
    Dict(k => f(A) for (k, A) in attractors)
end
```

with `f` your function of interest that returns a real number.

## Keyword arguments

  * `series_kwargs`: named tuple of arguments propagated to `Makie.scatterlines!` that plots the curves.
  * Also all [common plotting keywords](@ref common_plot_kwargs).
