```julia
asgraph(sys::AbstractSystem; variables = states(sys),
        variablestoids = Dict(convert(Variable, v) => i for (i, v) in enumerate(variables)))
```

Convert an `AbstractSystem` to a [`BipartiteGraph`](@ref) mapping the index of equations to the indices of variables they depend on.

Notes:

  * Defaults for kwargs creating a mapping from `equations(sys)` to `states(sys)` they depend on.
  * `variables` should provide the list of variables to use for generating the dependency graph.
  * `variablestoids` should provide `Dict` like mapping from a `Variable` to its `Int` index within `variables`.

Example: Continuing the example started in [`equation_dependencies`](@ref)

```julia
digr = asgraph(jumpsys)
```
