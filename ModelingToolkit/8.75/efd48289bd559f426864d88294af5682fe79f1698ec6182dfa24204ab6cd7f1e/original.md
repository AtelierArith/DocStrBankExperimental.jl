```julia
asdigraph(g::BipartiteGraph, sys::AbstractSystem; variables = states(sys),
          equationsfirst = true)
```

Convert a [`BipartiteGraph`](@ref) to a `LightGraph.SimpleDiGraph`.

Notes:

  * The resulting `SimpleDiGraph` unifies the two sets of vertices (equations and then states in the case it comes from [`asgraph`](@ref)), producing one ordered set of integer vertices (`SimpleDiGraph` does not support two distinct collections of vertices, so they must be merged).
  * `variables` gives the variables that `g` are associated with (usually the `states` of a system).
  * `equationsfirst` (default is `true`) gives whether the [`BipartiteGraph`](@ref) gives a mapping from equations to variables they depend on (`true`), as calculated by [`asgraph`](@ref), or whether it gives a mapping from variables to the equations that modify them, as calculated by [`variable_dependencies`](@ref).

Example: Continuing the example in [`asgraph`](@ref)

```julia
dg = asdigraph(digr, jumpsys)
```
