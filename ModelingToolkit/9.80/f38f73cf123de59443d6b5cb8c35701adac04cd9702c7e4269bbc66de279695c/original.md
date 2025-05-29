```julia
eqeq_dependencies(eqdeps::BipartiteGraph{T},
                  vardeps::BipartiteGraph{T}) where {T <: Integer}
```

Calculate a `LightGraph.SimpleDiGraph` that maps each equation to equations they depend on.

Notes:

  * The `fadjlist` of the `SimpleDiGraph` maps from an equation to the equations that modify variables it depends on.
  * The `badjlist` of the `SimpleDiGraph` maps from an equation to equations that depend on variables it modifies.

Example: Continuing the example of `equation_dependencies`

```julia
eqeqdep = eqeq_dependencies(asgraph(jumpsys), variable_dependencies(jumpsys))
```
