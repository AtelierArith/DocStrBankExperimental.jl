```julia
function varvar_dependencies(eqdeps::BipartiteGraph{T},
                             vardeps::BipartiteGraph{T}) where {T <: Integer}
    eqeq_dependencies(vardeps, eqdeps)
end
```

Calculate a `LightGraph.SimpleDiGraph` that maps each variable to variables they depend on.

Notes:

  * The `fadjlist` of the `SimpleDiGraph` maps from a variable to the variables that depend on it.
  * The `badjlist` of the `SimpleDiGraph` maps from a variable to variables on which it depends.

Example: Continuing the example of `equation_dependencies`

```julia
varvardep = varvar_dependencies(asgraph(jumpsys), variable_dependencies(jumpsys))
```
