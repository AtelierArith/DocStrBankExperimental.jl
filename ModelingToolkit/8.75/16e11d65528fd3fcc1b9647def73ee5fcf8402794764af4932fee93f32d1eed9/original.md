```julia
asgraph(eqdeps, vtois)
```

Convert a collection of equation dependencies, for example as returned by `equation_dependencies`, to a [`BipartiteGraph`](@ref).

Notes:

  * `vtois` should provide a `Dict` like mapping from each `Variable` dependency in `eqdeps` to the integer idx of the variable to use in the graph.

Example: Continuing the example started in [`equation_dependencies`](@ref)

```julia
digr = asgraph(equation_dependencies(jumpsys),
               Dict(s => i for (i, s) in enumerate(states(jumpsys))))
```
